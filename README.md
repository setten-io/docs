---
description: Documentation for Setten services and tools.
---

# What is Setten

Setten is Blockchain as a Service company dedicated to the Terra blockchain.

With Setten, you can access the Terra network with fast and reliable performance in only a few clicks. Spend less time on your infrastructure and more time building your project.

{% hint style="info" %}
**Are you looking for feature requests and community discussions?**

You can request and vote for features, give feedback, and receive community support [here](https://github.com/orgs/setten-io/discussions). Talk to you soon!
{% endhint %}

## Get started in two minutes

### Developer

<details>

<summary>Create and account</summary>

1. Log in with Github or register on our [app](https://app.setten.io/login).

</details>

<details>

<summary>Create a new project</summary>

1. On the [Projects](https://app.setten.io/projects) page, click on [Add project](https://app.setten.io/projects/create).
2. Give it a descriptive name and click on "Create".
3. You will be redirected to your new project page.

</details>

<details>

<summary>Get your project id and key</summary>

1. In the "Access" section, copy the "Project ID" and "Key" fields.

</details>

<details>

<summary>Use your project endpoint in your code</summary>

{% code title="javascript" %}
```javascript
import { LCDClient } from '@terra-money/terra.js';

const settenProject = "37677fb03e7d426e8ecfd56f36655577"
const settenKey = "4e4a6106c6354339a263d23090559804"

// connect to pisco testnet
const terra = new LCDClient({
  URL: `https://lcd.pisco.terra.setten.io/${settenProject}?key=${settenKey}`,
  chainID: 'pisco-1',
});

// ...
```
{% endcode %}

{% code title="python" %}
```python
import asyncio

from terra_sdk.client.lcd import AsyncLCDClient

SETTEN_PROJECT = "37677fb03e7d426e8ecfd56f36655577"
SETTEN_KEY = "4e4a6106c6354339a263d23090559804"


async def main():
    terra = AsyncLCDClient(f"https://lcd.pisco.terra.setten.io/{SETTEN_PROJECT}", "pisco-1")
    terra.session.headers.add("Authorization", f"Bearer {SETTEN_KEY}")
    # ...
    await terra.session.close()

asyncio.get_event_loop().run_until_complete(main())
```
{% endcode %}

</details>

## Guides

Not sure where to start? Check out our guide to set your project on foot:

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}

## Concepts

Deep dive into Setten's architecture:

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}
