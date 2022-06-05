---
description: Use Setten with the main Terra SDKs
---

# SDKs

Let's look at how easy it is to use our LCD endpoints with any existing Terra SDK/tooling by updating their documentation example to use Setten.

## Terra.js

{% hint style="info" %}
Terra.js does not support custom headers or query strings yet.

We recommend using basic auth for the time being as shown in this example and described in [Authentication](https://docs.setten.io/concepts/authentication#3.-basic-auth).
{% endhint %}

```javascript
import { LCDClient, Coin } from '@terra-money/terra.js';

const settenProject = "37677fb03e7d426e8ecfd56f36655577"
const settenKey = "4e4a6106c6354339a263d23090559804"

// connect to pisco testnet
const terra = new LCDClient({
  URL: `https://lcd.pisco.terra.setten.io/${settenProject}?key=${settenKey}`,
  chainID: 'pisco-1',
});

// ...
```

## Terra.py

### async

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

### sync

{% hint style="info" %}
Terra.py synchronous `LCDClient` does not support custom headers or query strings yet.

We recommend using the [async ](sdks.md#async)client until we solve this with the TFL team.
{% endhint %}
