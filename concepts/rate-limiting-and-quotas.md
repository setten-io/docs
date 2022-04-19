---
description: Rate limiting and quotas across our infrastructure
---

# Rate limiting and quotas

Limiting the number of requests each user can make in a specific time frame gives us more control over the sizing of the infrastructure. Which helps us deliver the highest level of service to all of our users, ensuring there are always enough resources to process the incoming transactions.

We protect our endpoints with two kinds of limits: Burst rate-limiting and quotas.

To know which limits apply to your account, please refer to [Plans](plans.md).

### Bust rate-limiting - short time frame

{% hint style="warning" %}
Please note that both burst rate-limiting and quotas apply to each account globally, not individual projects.

If a project is getting rate-limited from sending too many requests, it will affect all the other projects under the same account.
{% endhint %}

{% hint style="info" %}
When blocked by our burst rate-limiting, it will return a `retry-after` header. It contains the number of seconds left before being unblocked.
{% endhint %}

Burst rate-limiting ensures there aren't too many requests coming at once from a single user in a few seconds.

### Quotas - long time frame

{% hint style="info" %}
All the responses from our endpoints contain custom headers with quota information.

`X-Setten-Quota`: Account total quota for the current billing period.

`X-Setten-Remaining`: Remaining requests for the current billing period.
{% endhint %}

Quotas regulate users' API consumption over a more extended period (usually in days/weeks/months).
