---
description: Authentication for Setten projects
---

# Authentication

Each of your projects has its endpoint and key for authentication. This design gives the user a granular approach to security. If necessary, it is effortless to remove or cycle a project key without affecting other projects.

{% hint style="info" %}
If you are searching for a way to authenticate in a client that only accepts an URL, like Terrain for example, please see [Basic auth](authentication.md#3.-basic-auth)
{% endhint %}

## Authentication process

When receiving requests, we will always verify their authenticity via these simple steps:

1. Get the `project_id` from the first segment of the URL's path
2. Retrieve the `key` from the locations described in [Project key locations](authentication.md#project-key-locations)
3. If `key` is the key registered for the project with id `project_id` the request is proxied

### Project key locations

Those are the locations we'll check for your project key in order. Only the first matched key will be used for authentication.

#### 1. Header

A header named `X-Setten-Key`.

{% tabs %}
{% tab title="curl" %}
```bash
PROJECT="37677fb03e7d426e8ecfd56f36655577"
KEY="4e4a6106c6354339a263d23090559804"

curl https://bombay.lcd.setten.io/${PROJECT}/node_info \
     -H "X-Setten-Key: ${KEY}"
```
{% endtab %}

{% tab title="python 3" %}
```python
import requests

project_id = "37677fb03e7d426e8ecfd56f36655577"
headers = {"X-Setten-Key": "4e4a6106c6354339a263d23090559804"}

requests.get(f"https://bombay.lcd.setten.io/{project_id}/node_info", headers=headers )
```
{% endtab %}

{% tab title="javascript" %}
```javascript
const projectId = "37677fb03e7d426e8ecfd56f36655577"
const headers = {"X-Setten-Key": "4e4a6106c6354339a263d23090559804"}

fetch(`https://bombay.lcd.setten.io/${projectId}/node_info`, { headers })
```
{% endtab %}
{% endtabs %}

#### 2. Query string

A query string named `key`.

{% tabs %}
{% tab title="curl" %}
```bash
PROJECT="37677fb03e7d426e8ecfd56f36655577"
KEY="4e4a6106c6354339a263d23090559804"

curl https://bombay.lcd.setten.io/${PROJECT}/node_info?key=${KEY}
```
{% endtab %}

{% tab title="python 3" %}
```python
import requests

project_id = "37677fb03e7d426e8ecfd56f36655577"
key = "4e4a6106c6354339a263d23090559804"

requests.get(f"https://bombay.lcd.setten.io/{project_id}/node_info?key={key}")
```
{% endtab %}

{% tab title="javascript" %}
```javascript
const projectId = "37677fb03e7d426e8ecfd56f36655577"
const key = "4e4a6106c6354339a263d23090559804"

fetch(`https://bombay.lcd.setten.io/${projectId}/node_info?key=${key}`)
```
{% endtab %}
{% endtabs %}

#### 3. Basic auth

Basic auth with no username and the project key as the password.

{% hint style="warning" %}
**If you are querying the API from code, you probably should use one of the two first techniques.**

Basic auth is only sound when using a client that only accepts an URL and doesn't offer the possibility to inject headers or query strings
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```bash
PROJECT="37677fb03e7d426e8ecfd56f36655577"
KEY="4e4a6106c6354339a263d23090559804"

curl https://:${KEY}@bombay.lcd.setten.io/${PROJECT}/node_info
```
{% endtab %}

{% tab title="python 3" %}
```python
import requests

project_id = "37677fb03e7d426e8ecfd56f36655577"
key = "4e4a6106c6354339a263d23090559804"

requests.get(f"https://:{key}@bombay.lcd.setten.io/{project_id}/node_info")
```
{% endtab %}

{% tab title="javascript" %}
```javascript
const projectId = "37677fb03e7d426e8ecfd56f36655577"
const key = "4e4a6106c6354339a263d23090559804"

fetch(`https://:${key}@bombay.lcd.setten.io/${projectId}/node_info`)
```
{% endtab %}
{% endtabs %}
