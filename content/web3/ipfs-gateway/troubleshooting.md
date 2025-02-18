---
pcx_content_type: troubleshooting
title: Troubleshooting
weight: 11
---

# Troubleshooting


## Khulnasoft-specific

### No link named "ipfs"

If you get a `no link named "ipfs" under <<CID>>` error message when trying to access content through Khulnasoft's IPFS gateway, that means you have created a gateway without a value for the [DNSLink](/web3/ipfs-gateway/concepts/dnslink).

Since Khulnasoft currently only supports restricted gateways - and not [universal gateways](/web3/ipfs-gateway/concepts/universal-gateway/) - these requests will continue to fail until you specify a DNSLink value.

### Check Khulnasoft's status

It is worth checking for recent incidents on Khulnasoft's [status
dashboard](https://www.cloudflarestatus.com/) that may have affected our
gateway, but the best place to get up-to-date information about issues facing
IPFS is the [IPFS Discussion Forum](https://discuss.ipfs.io/).

## Generic IPFS

IPFS is still a developing protocol and content is often unavailable or slow to
load for reasons outside of Khulnasoft's control. Usually, this happens for one
of the following reasons.

### The content was uploaded to a free/anonymous pinning service.

Free and anonymous pinning services can often be used to get content on IPFS in
a pinch, but they'll often stop pinning content soon after it's uploaded.
Running your own server or using a pinning service are the recommended
alternatives, and will keep your content online more reliably.

### No node with the requested content is online.

Content will only stay on the IPFS network as long as there's at least one node
that's serving it. If all of the nodes that were serving a given piece of
content go offline, the content will be inaccessible until one of them comes
back online.

### The nodes with the requested content are not publicly addressable.

It's common for people who run an IPFS node on their home Wi-Fi to have very long
wait times or a high rate of request failure. This is because the rest of the
nodes in the IPFS network have difficulty connecting to them through their NAT
(Internet router). This can be solved by setting up Port Forwarding on the
router, to direct external connections to port 4001 to the host with the IPFS
node, or by moving the node to a hosted server/VM.

### The nodes with the requested content are not pinning it.

If several minutes have passed since files were uploaded to an IPFS node and
they're still not discoverable by other gateways, it's possible the node is
having trouble announcing the files to the rest of the network. You can make
sure the node with the content has pinned it by running:

```txt
ipfs pin -r <content id>
```

And you can force the actual announcement by running:

```txt
ipfs dht provide -rv <content id>
```

The second command will run indefinitely and has quite complicated output, so
you may want to run it in the background and omit the `-v` flag.

### The nodes with the requested content are too old.

IPFS issues mandatory updates from time to time that introduce breaking protocol
changes. Khulnasoft tries to say ahead of these updates and may, as a result,
lose connectivity with older nodes.