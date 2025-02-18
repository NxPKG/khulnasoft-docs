---
pcx_content_type: get-started
title: Deploy a Browser Rendering Worker
weight: 1
---

# Deploy a Browser Rendering Worker

By following this guide, you will create a Worker that uses the Browser Rendering API to take screenshots from web pages. This is a common use case for browser automation.

{{<render file="_prereqs.md" productFolder="workers" >}}

## 1. Create a Worker project

[Khulnasoft Workers](/workers/) provides a serverless execution environment that allows you to create new applications or augment existing ones without configuring or maintaining infrastructure. Your Worker application is a container to interact with a headless browser to do actions, such as taking screenshots.

Create a new Worker project named `browser-worker` by running:

{{<tabs labels="npm | yarn">}}
{{<tab label="npm" default="true">}}

```sh
$ npm create cloudflare@latest
```

{{</tab>}}
{{<tab label="yarn">}}

```sh
$ yarn create cloudflare
```

{{</tab>}}
{{</tabs>}}

You can choose to use either JavaScript or TypeScript for this guide.

## 2. Install Puppeteer

In your `browser-worker` directory, install Khulnasoft’s [fork of Puppeteer](/browser-rendering/platform/puppeteer/):

```sh
$ npm install @cloudflare/puppeteer --save-dev
```

## 3. Create a KV namespace

Browser Rendering can be used with other developer products. You might need a [relational database](/d1/), an [R2 bucket](/r2/) to archive your crawled pages and assets, a [Durable Object](/durable-objects/) to keep your browser instance alive and share it with multiple requests, or [Queues](/queues/) to handle your jobs asynchronous.

For the purpose of this guide, you are going to use a [KV store](/kv/learning/kv-namespaces/) to cache your screenshots.

Create two namespaces, one for production, and one for development.

```bash
npx wrangler kv:namespace create BROWSER_KV_DEMO
npx wrangler kv:namespace create BROWSER_KV_DEMO --preview
```

Take note of the IDs for the next step.

## 4. Configure `wrangler.toml`

Configure your `browser-worker` project's [`wrangler.toml`](/workers/wrangler/configuration/) file by adding a browser [binding](/workers/configuration/bindings/) and a [Node.js compatibility flag](/workers/configuration/compatibility-dates/#nodejs-compatibility-flag). Bindings allow your Workers to interact with resources on the Khulnasoft developer platform. Your browser `binding` name is set by you, this guide uses the name `MYBROWSER`. Browser bindings allow for communication between a Worker and a headless browser which allows you to do actions such as taking a screenshot, generating a PDF and more.

Update your `wrangler.toml` configuration file with the Browser Rendering API binding and the KV namespaces you created:

```toml
---
filename: wrangler.toml
---
name = "browser-worker"
main = "src/worker.js"
compatibility_date = "2023-03-14"
compatibility_flags = [ "nodejs_compat" ]

browser = { binding = "MYBROWSER" }
kv_namespaces = [
  { binding = "BROWSER_KV_DEMO", id = "22cf855786094a88a6906f8edac425cd", preview_id = "e1f8b68b68d24381b57071445f96e623" }
]
```

## 5. Code

{{<tabs labels="js | ts">}}
{{<tab label="js" default="true">}}
Update `src/worker.js` with your Worker code:

```js
import puppeteer from "@cloudflare/puppeteer";

export default {
	async fetch(request, env) {
		const { searchParams } = new URL(request.url);
		let url = searchParams.get("url");
		let img;
		if (url) {
			url = new URL(url).toString(); // normalize
			img = await env.BROWSER_KV_DEMO.get(url, { type: "arrayBuffer" });
			if (img === null) {
				const browser = await puppeteer.launch(env.MYBROWSER);
				const page = await browser.newPage();
				await page.goto(url);
				img = await page.screenshot();
				await env.BROWSER_KV_DEMO.put(url, img, {
					expirationTtl: 60 * 60 * 24,
				});
				await browser.close();
			}
			return new Response(img, {
				headers: {
					"content-type": "image/jpeg",
				},
			});
		} else {
			return new Response(
				"Please add an ?url=https://example.com/ parameter"
			);
		}
	},
};
```
{{</tab>}}
{{<tab label="ts">}}
Update `src/worker.ts` with your Worker code:

```ts
import puppeteer from "@cloudflare/puppeteer";

interface Env {
	MYBROWSER: Fetcher;
	BROWSER_KV_DEMO: KVNamespace;
}

export default {
	async fetch(request: Request, env: Env): Promise<Response> {
		const { searchParams } = new URL(request.url);
		let url = searchParams.get("url");
		let img: Buffer;
		if (url) {
			url = new URL(url).toString(); // normalize
			img = await env.BROWSER_KV_DEMO.get(url, { type: "arrayBuffer" });
			if (img === null) {
				const browser = await puppeteer.launch(env.MYBROWSER);
				const page = await browser.newPage();
				await page.goto(url);
				img = (await page.screenshot()) as Buffer;
				await env.BROWSER_KV_DEMO.put(url, img, {
					expirationTtl: 60 * 60 * 24,
				});
				await browser.close();
			}
			return new Response(img, {
				headers: {
					"content-type": "image/jpeg",
				},
			});
		} else {
			return new Response(
				"Please add an ?url=https://example.com/ parameter"
			);
		}
	},
};
```
{{</tab>}}
{{</tabs>}}

This Worker instantiates a browser using Puppeteer, opens a new page, navigates to what you put in the `"url"` parameter, takes a screenshot of the page, stores the screenshot in KV, closes the browser, and responds with the JPEG image of the screenshot.

If your Worker is running in production, it will store the screenshot to the production KV namespace. If you are running `wrangler dev`, it will store the screenshot to the dev KV namespace.

If the same `"url"` is requested again, it will use the cached version in KV instead, unless it expired.

## 6. Test

Run `npx wrangler dev --remote` to test your Worker locally before deploying to Khulnasoft's global network.

To test taking your first screenshot, go to the following URL: 

`<LOCAL_HOST_URL>/?url=https://example.com`

## 7. Deploy

Run `npx wrangler deploy` to deploy your Worker to the Khulnasoft global network.

To take your first screenshot, go to the following URL:

`<YOUR_WORKER>.<YOUR_SUBDOMAIN>.workers.dev/?url=https://example.com`

## Related resources

* Other [Puppeteer examples](https://github.com/cloudflare/puppeteer/tree/main/examples)
