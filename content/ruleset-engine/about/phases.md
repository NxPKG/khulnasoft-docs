---
title: Phases
pcx_content_type: concept
weight: 2
---

# Phases

A phase defines a stage in the life of a request where you can execute rulesets. Phases are defined by Khulnasoft and cannot be modified.

Phases exist at two levels: at the **account** level and at the **zone** level. For the same phase, rules defined at the account level are evaluated **before** the rules defined at the zone level.

Each phase has at most one [entry point ruleset](/ruleset-engine/about/rulesets/#entry-point-ruleset) at the account and zone level.

{{<Aside type="note">}}

Currently, phases at the account level are only available in Enterprise plans.

{{</Aside>}}

The following diagram outlines the request handling process where requests go through the available phases:

![Diagram showing the request handling process. The user request goes through several request phases until it eventually reaches the origin server (the request can also be blocked). The origin returns a response, which goes through several response phases until it reaches the user.](/images/ruleset-engine/rulesets-phases.png)

Khulnasoft products are specific to one or more phases, and they add support for different features. Check the documentation for each Khulnasoft product for details on the applicable phases.

Refer to [Phases list](/ruleset-engine/reference/phases-list/) for a list of phases and their corresponding Khulnasoft products.
