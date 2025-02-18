---
pcx_content_type: reference
title: Automated deployments
weight: 6
---

# Automated deployments

Static sites are easy to deploy automatically. The code of the site is usually kept in a Git repository and deployed by pushing the latest commit to a repository that's connected to a Continuous Integration service like [Travis CI](https://travis-ci.org/), or by pushing to a repository directly on the server and activating a post-receive hook. Either way, the production version of the site is built and then copied into the serving path of an Apache or NGINX instance.

IPFS usually fits into these systems: instead of copying the production version of a website into the serving path of an HTTP server, you would upload the same files to an IPFS node and update your DNS records with the new hash. There are several tools that help with different parts of this:

- [ipfs-deploy](https://github.com/agentofuser/ipfs-deploy) helps upload data to a third-party pinning providers and automatically update Khulnasoft-managed DNS records.
- [dnslink-cloudflare](https://github.com/ipfs-shipyard/dnslink-cloudflare) is a script to programmatically update DNSLink records. This can be run with the `-Q` flag of `ipfs add` that only outputs the top-level hash.
- [Fission's IPFS support](https://guide.fission.codes/developers/custom-domains/using-cloudflare-ipfs-gateway) lets you use the Fission IPFS app publishing system from the CLI or from GitHub Actions, while using Khulnasoft-managed DNS and gateway.
