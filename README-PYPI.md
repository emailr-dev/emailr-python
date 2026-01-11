# emailr

Developer-friendly & type-safe Python SDK specifically catered to leverage *emailr* API.

[![Built by Speakeasy](https://img.shields.io/badge/Built_by-SPEAKEASY-374151?style=for-the-badge&labelColor=f3f4f6)](https://www.speakeasy.com/?utm_source=emailr&utm_campaign=python)
[![License: MIT](https://img.shields.io/badge/LICENSE_//_MIT-3b5bdb?style=for-the-badge&labelColor=eff6ff)](https://opensource.org/licenses/MIT)


<br /><br />
> [!IMPORTANT]
> This SDK is not yet ready for production use. To complete setup please follow the steps outlined in your [workspace](https://app.speakeasy.com/org/hormo/emailr). Delete this section before > publishing to a package manager.

<!-- Start Summary [summary] -->
## Summary


<!-- End Summary [summary] -->

<!-- Start Table of Contents [toc] -->
## Table of Contents
<!-- $toc-max-depth=2 -->
* [emailr](https://github.com/emailr-dev/emailr-python/blob/master/#emailr)
  * [SDK Installation](https://github.com/emailr-dev/emailr-python/blob/master/#sdk-installation)
  * [IDE Support](https://github.com/emailr-dev/emailr-python/blob/master/#ide-support)
  * [SDK Example Usage](https://github.com/emailr-dev/emailr-python/blob/master/#sdk-example-usage)
  * [Authentication](https://github.com/emailr-dev/emailr-python/blob/master/#authentication)
  * [Available Resources and Operations](https://github.com/emailr-dev/emailr-python/blob/master/#available-resources-and-operations)
  * [Retries](https://github.com/emailr-dev/emailr-python/blob/master/#retries)
  * [Error Handling](https://github.com/emailr-dev/emailr-python/blob/master/#error-handling)
  * [Server Selection](https://github.com/emailr-dev/emailr-python/blob/master/#server-selection)
  * [Custom HTTP Client](https://github.com/emailr-dev/emailr-python/blob/master/#custom-http-client)
  * [Resource Management](https://github.com/emailr-dev/emailr-python/blob/master/#resource-management)
  * [Debugging](https://github.com/emailr-dev/emailr-python/blob/master/#debugging)
* [Development](https://github.com/emailr-dev/emailr-python/blob/master/#development)
  * [Maturity](https://github.com/emailr-dev/emailr-python/blob/master/#maturity)
  * [Contributions](https://github.com/emailr-dev/emailr-python/blob/master/#contributions)

<!-- End Table of Contents [toc] -->

<!-- Start SDK Installation [installation] -->
## SDK Installation

> [!NOTE]
> **Python version upgrade policy**
>
> Once a Python version reaches its [official end of life date](https://devguide.python.org/versions/), a 3-month grace period is provided for users to upgrade. Following this grace period, the minimum python version supported in the SDK will be updated.

The SDK can be installed with *uv*, *pip*, or *poetry* package managers.

### uv

*uv* is a fast Python package installer and resolver, designed as a drop-in replacement for pip and pip-tools. It's recommended for its speed and modern Python tooling capabilities.

```bash
uv add emailr
```

### PIP

*PIP* is the default package installer for Python, enabling easy installation and management of packages from PyPI via the command line.

```bash
pip install emailr
```

### Poetry

*Poetry* is a modern tool that simplifies dependency management and package publishing by using a single `pyproject.toml` file to handle project metadata and dependencies.

```bash
poetry add emailr
```

### Shell and script usage with `uv`

You can use this SDK in a Python shell with [uv](https://docs.astral.sh/uv/) and the `uvx` command that comes with it like so:

```shell
uvx --from emailr python
```

It's also possible to write a standalone Python script without needing to set up a whole project like so:

```python
#!/usr/bin/env -S uv run --script
# /// script
# requires-python = ">=3.9"
# dependencies = [
#     "emailr",
# ]
# ///

from emailr import Emailr

sdk = Emailr(
  # SDK arguments
)

# Rest of script here...
```

Once that is saved to a file, you can run it with `uv run script.py` where
`script.py` can be replaced with the actual file name.
<!-- End SDK Installation [installation] -->

<!-- Start IDE Support [idesupport] -->
## IDE Support

### PyCharm

Generally, the SDK will work well with most IDEs out of the box. However, when using PyCharm, you can enjoy much better integration with Pydantic by installing an additional plugin.

- [PyCharm Pydantic Plugin](https://docs.pydantic.dev/latest/integrations/pycharm/)
<!-- End IDE Support [idesupport] -->

<!-- Start SDK Example Usage [usage] -->
## SDK Example Usage

### Example

```python
# Synchronous Example
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.emails.send(request={
        "from_": "sender@example.com",
        "to": "recipient@example.com",
        "subject": "Hello World",
        "html": "<h1>Hello</h1>",
        "text": "Hello",
        "template_id": "123e4567-e89b-12d3-a456-426614174000",
        "template_data": {
            "name": "John",
            "company": "Acme",
        },
        "tags": {
            "campaign": "welcome",
            "source": "signup",
        },
        "attachments": [
            {
                "filename": "document.pdf",
                "content": "JVBERi0xLjQKJe...",
                "content_type": "application/pdf",
            },
        ],
        "reply_to": {
            "in_reply_to": "<message-id@domain.com>",
            "thread_id": "123e4567-e89b-12d3-a456-426614174000",
            "parent_email_id": "123e4567-e89b-12d3-a456-426614174000",
        },
        "reply_to_email": "support@example.com",
        "preview_text": "Check out our latest updates...",
    })

    # Handle response
    print(res)
```

</br>

The same SDK client can also be used to make asynchronous requests by importing asyncio.

```python
# Asynchronous Example
import asyncio
from emailr import Emailr
import os

async def main():

    async with Emailr(
        bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
    ) as e_client:

        res = await e_client.emails.send_async(request={
            "from_": "sender@example.com",
            "to": "recipient@example.com",
            "subject": "Hello World",
            "html": "<h1>Hello</h1>",
            "text": "Hello",
            "template_id": "123e4567-e89b-12d3-a456-426614174000",
            "template_data": {
                "name": "John",
                "company": "Acme",
            },
            "tags": {
                "campaign": "welcome",
                "source": "signup",
            },
            "attachments": [
                {
                    "filename": "document.pdf",
                    "content": "JVBERi0xLjQKJe...",
                    "content_type": "application/pdf",
                },
            ],
            "reply_to": {
                "in_reply_to": "<message-id@domain.com>",
                "thread_id": "123e4567-e89b-12d3-a456-426614174000",
                "parent_email_id": "123e4567-e89b-12d3-a456-426614174000",
            },
            "reply_to_email": "support@example.com",
            "preview_text": "Check out our latest updates...",
        })

        # Handle response
        print(res)

asyncio.run(main())
```
<!-- End SDK Example Usage [usage] -->

<!-- Start Authentication [security] -->
## Authentication

### Per-Client Security Schemes

This SDK supports the following security scheme globally:

| Name          | Type | Scheme      | Environment Variable |
| ------------- | ---- | ----------- | -------------------- |
| `bearer_auth` | http | HTTP Bearer | `EMAILR_BEARER_AUTH` |

To authenticate with the API the `bearer_auth` parameter must be set when initializing the SDK client instance. For example:
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.emails.send(request={
        "from_": "sender@example.com",
        "to": "recipient@example.com",
        "subject": "Hello World",
        "html": "<h1>Hello</h1>",
        "text": "Hello",
        "template_id": "123e4567-e89b-12d3-a456-426614174000",
        "template_data": {
            "name": "John",
            "company": "Acme",
        },
        "tags": {
            "campaign": "welcome",
            "source": "signup",
        },
        "attachments": [
            {
                "filename": "document.pdf",
                "content": "JVBERi0xLjQKJe...",
                "content_type": "application/pdf",
            },
        ],
        "reply_to": {
            "in_reply_to": "<message-id@domain.com>",
            "thread_id": "123e4567-e89b-12d3-a456-426614174000",
            "parent_email_id": "123e4567-e89b-12d3-a456-426614174000",
        },
        "reply_to_email": "support@example.com",
        "preview_text": "Check out our latest updates...",
    })

    # Handle response
    print(res)

```
<!-- End Authentication [security] -->

<!-- Start Available Resources and Operations [operations] -->
## Available Resources and Operations

<details open>
<summary>Available methods</summary>

### [ApiKeys](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/apikeys/README.md)

* [create](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/apikeys/README.md#create) - Create API key
* [list](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/apikeys/README.md#list) - List API keys
* [revoke](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/apikeys/README.md#revoke) - Revoke API key

### [Billing](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/billing/README.md)

* [post_v1_billing_checkout](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/billing/README.md#post_v1_billing_checkout)
* [post_v1_billing_portal](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/billing/README.md#post_v1_billing_portal)
* [get_v1_billing_usage](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/billing/README.md#get_v1_billing_usage)
* [post_v1_billing_webhooks](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/billing/README.md#post_v1_billing_webhooks)

### [Broadcasts](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/broadcasts/README.md)

* [create](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/broadcasts/README.md#create) - Create broadcast
* [list](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/broadcasts/README.md#list) - List broadcasts
* [send](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/broadcasts/README.md#send) - Send broadcast
* [get](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/broadcasts/README.md#get) - Get broadcast

### [ContactSync](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/contactsync/README.md)

* [post_v1_contact_sync_supabase](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/contactsync/README.md#post_v1_contact_sync_supabase)
* [post_v1_contact_sync_webhook_sync_id_](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/contactsync/README.md#post_v1_contact_sync_webhook_sync_id_)
* [get_v1_contact_sync](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/contactsync/README.md#get_v1_contact_sync)
* [delete_v1_contact_sync_id_](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/contactsync/README.md#delete_v1_contact_sync_id_)

### [Contacts](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/contacts/README.md)

* [create](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/contacts/README.md#create) - Create a contact
* [list](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/contacts/README.md#list) - List contacts
* [bulk_create](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/contacts/README.md#bulk_create) - Bulk create contacts
* [get](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/contacts/README.md#get) - Get contact
* [update](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/contacts/README.md#update) - Update contact
* [delete](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/contacts/README.md#delete) - Delete contact

### [Domains](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/domains/README.md)

* [add](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/domains/README.md#add) - Add domain
* [list](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/domains/README.md#list) - List domains
* [verify](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/domains/README.md#verify) - Verify domain
* [get_dns_status](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/domains/README.md#get_dns_status) - Get DNS status
* [update](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/domains/README.md#update) - Update domain
* [delete](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/domains/README.md#delete) - Delete domain

### [Emails](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/emails/README.md)

* [send](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/emails/README.md#send) - Send an email
* [get](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/emails/README.md#get) - Get email by ID
* [list](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/emails/README.md#list) - List emails

### [Integrations](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/integrations/README.md)

* [get_v1_integrations_connections](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/integrations/README.md#get_v1_integrations_connections)
* [get_v1_integrations_supabase_authorize](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/integrations/README.md#get_v1_integrations_supabase_authorize)
* [get_v1_integrations_supabase_callback](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/integrations/README.md#get_v1_integrations_supabase_callback)
* [delete_v1_integrations_id_](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/integrations/README.md#delete_v1_integrations_id_)
* [get_v1_integrations_vercel_authorize](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/integrations/README.md#get_v1_integrations_vercel_authorize)
* [get_v1_integrations_vercel_callback](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/integrations/README.md#get_v1_integrations_vercel_callback)

### [Logs](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/logs/README.md)

* [list](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/logs/README.md#list) - Get email logs

### [Metrics](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/metrics/README.md)

* [get_usage](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/metrics/README.md#get_usage) - Get usage metrics
* [get_emails](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/metrics/README.md#get_emails) - Get email metrics

### [Segments](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/segments/README.md)

* [create](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/segments/README.md#create) - Create segment
* [list](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/segments/README.md#list) - List segments
* [add_contact](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/segments/README.md#add_contact) - Add contact to segment

### [Settings](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/settings/README.md)

* [get_organization](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/settings/README.md#get_organization) - Get organization settings
* [update_organization](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/settings/README.md#update_organization) - Update organization settings
* [get_team](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/settings/README.md#get_team) - Get team members
* [get_unsubscribe](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/settings/README.md#get_unsubscribe) - Get unsubscribe settings
* [update_unsubscribe](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/settings/README.md#update_unsubscribe) - Update unsubscribe settings

### [Smtp](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/smtp/README.md)

* [get_smtp_credentials](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/smtp/README.md#get_smtp_credentials) - Get SMTP credentials

### [Templates](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/templates/README.md)

* [create](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/templates/README.md#create) - Create a template
* [list](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/templates/README.md#list) - List templates
* [get](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/templates/README.md#get) - Get template
* [update](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/templates/README.md#update) - Update template
* [delete](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/templates/README.md#delete) - Delete template

### [Topics](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/topics/README.md)

* [get_v1_topics](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/topics/README.md#get_v1_topics)
* [post_v1_topics](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/topics/README.md#post_v1_topics)
* [put_v1_topics_id_](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/topics/README.md#put_v1_topics_id_)
* [delete_v1_topics_id_](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/topics/README.md#delete_v1_topics_id_)

### [Unsubscribe](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/unsubscribe/README.md)

* [get_v1_unsubscribe_organization_id_](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/unsubscribe/README.md#get_v1_unsubscribe_organization_id_)
* [post_v1_unsubscribe](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/unsubscribe/README.md#post_v1_unsubscribe)

### [Webhooks](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/webhooks/README.md)

* [create](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/webhooks/README.md#create) - Create webhook
* [list](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/webhooks/README.md#list) - List webhooks
* [toggle](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/webhooks/README.md#toggle) - Toggle webhook
* [delete](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/webhooks/README.md#delete) - Delete webhook
* [list_deliveries](https://github.com/emailr-dev/emailr-python/blob/master/docs/sdks/webhooks/README.md#list_deliveries) - Get webhook deliveries

</details>
<!-- End Available Resources and Operations [operations] -->

<!-- Start Retries [retries] -->
## Retries

Some of the endpoints in this SDK support retries. If you use the SDK without any configuration, it will fall back to the default retry strategy provided by the API. However, the default retry strategy can be overridden on a per-operation basis, or across the entire SDK.

To change the default retry strategy for a single API call, simply provide a `RetryConfig` object to the call:
```python
from emailr import Emailr
from emailr.utils import BackoffStrategy, RetryConfig
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.emails.send(request={
        "from_": "sender@example.com",
        "to": "recipient@example.com",
        "subject": "Hello World",
        "html": "<h1>Hello</h1>",
        "text": "Hello",
        "template_id": "123e4567-e89b-12d3-a456-426614174000",
        "template_data": {
            "name": "John",
            "company": "Acme",
        },
        "tags": {
            "campaign": "welcome",
            "source": "signup",
        },
        "attachments": [
            {
                "filename": "document.pdf",
                "content": "JVBERi0xLjQKJe...",
                "content_type": "application/pdf",
            },
        ],
        "reply_to": {
            "in_reply_to": "<message-id@domain.com>",
            "thread_id": "123e4567-e89b-12d3-a456-426614174000",
            "parent_email_id": "123e4567-e89b-12d3-a456-426614174000",
        },
        "reply_to_email": "support@example.com",
        "preview_text": "Check out our latest updates...",
    },
        RetryConfig("backoff", BackoffStrategy(1, 50, 1.1, 100), False))

    # Handle response
    print(res)

```

If you'd like to override the default retry strategy for all operations that support retries, you can use the `retry_config` optional parameter when initializing the SDK:
```python
from emailr import Emailr
from emailr.utils import BackoffStrategy, RetryConfig
import os


with Emailr(
    retry_config=RetryConfig("backoff", BackoffStrategy(1, 50, 1.1, 100), False),
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.emails.send(request={
        "from_": "sender@example.com",
        "to": "recipient@example.com",
        "subject": "Hello World",
        "html": "<h1>Hello</h1>",
        "text": "Hello",
        "template_id": "123e4567-e89b-12d3-a456-426614174000",
        "template_data": {
            "name": "John",
            "company": "Acme",
        },
        "tags": {
            "campaign": "welcome",
            "source": "signup",
        },
        "attachments": [
            {
                "filename": "document.pdf",
                "content": "JVBERi0xLjQKJe...",
                "content_type": "application/pdf",
            },
        ],
        "reply_to": {
            "in_reply_to": "<message-id@domain.com>",
            "thread_id": "123e4567-e89b-12d3-a456-426614174000",
            "parent_email_id": "123e4567-e89b-12d3-a456-426614174000",
        },
        "reply_to_email": "support@example.com",
        "preview_text": "Check out our latest updates...",
    })

    # Handle response
    print(res)

```
<!-- End Retries [retries] -->

<!-- Start Error Handling [errors] -->
## Error Handling

[`EmailrError`](https://github.com/emailr-dev/emailr-python/blob/master/./src/emailr/errors/emailrerror.py) is the base class for all HTTP error responses. It has the following properties:

| Property           | Type             | Description                                                                             |
| ------------------ | ---------------- | --------------------------------------------------------------------------------------- |
| `err.message`      | `str`            | Error message                                                                           |
| `err.status_code`  | `int`            | HTTP response status code eg `404`                                                      |
| `err.headers`      | `httpx.Headers`  | HTTP response headers                                                                   |
| `err.body`         | `str`            | HTTP body. Can be empty string if no body is returned.                                  |
| `err.raw_response` | `httpx.Response` | Raw HTTP response                                                                       |
| `err.data`         |                  | Optional. Some errors may contain structured data. [See Error Classes](https://github.com/emailr-dev/emailr-python/blob/master/#error-classes). |

### Example
```python
from emailr import Emailr, errors
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:
    res = None
    try:

        res = e_client.emails.send(request={
            "from_": "sender@example.com",
            "to": "recipient@example.com",
            "subject": "Hello World",
            "html": "<h1>Hello</h1>",
            "text": "Hello",
            "template_id": "123e4567-e89b-12d3-a456-426614174000",
            "template_data": {
                "name": "John",
                "company": "Acme",
            },
            "tags": {
                "campaign": "welcome",
                "source": "signup",
            },
            "attachments": [
                {
                    "filename": "document.pdf",
                    "content": "JVBERi0xLjQKJe...",
                    "content_type": "application/pdf",
                },
            ],
            "reply_to": {
                "in_reply_to": "<message-id@domain.com>",
                "thread_id": "123e4567-e89b-12d3-a456-426614174000",
                "parent_email_id": "123e4567-e89b-12d3-a456-426614174000",
            },
            "reply_to_email": "support@example.com",
            "preview_text": "Check out our latest updates...",
        })

        # Handle response
        print(res)


    except errors.EmailrError as e:
        # The base class for HTTP error responses
        print(e.message)
        print(e.status_code)
        print(e.body)
        print(e.headers)
        print(e.raw_response)

        # Depending on the method different errors may be thrown
        if isinstance(e, errors.Error):
            print(e.data.error)  # str
            print(e.data.code)  # Optional[str]
            print(e.data.details)  # OptionalNullable[Any]
```

### Error Classes
**Primary error:**
* [`EmailrError`](https://github.com/emailr-dev/emailr-python/blob/master/./src/emailr/errors/emailrerror.py): The base class for HTTP error responses.

<details><summary>Less common errors (18)</summary>

<br />

**Network errors:**
* [`httpx.RequestError`](https://www.python-httpx.org/exceptions/#httpx.RequestError): Base class for request errors.
    * [`httpx.ConnectError`](https://www.python-httpx.org/exceptions/#httpx.ConnectError): HTTP client was unable to make a request to a server.
    * [`httpx.TimeoutException`](https://www.python-httpx.org/exceptions/#httpx.TimeoutException): HTTP request timed out.


**Inherit from [`EmailrError`](https://github.com/emailr-dev/emailr-python/blob/master/./src/emailr/errors/emailrerror.py)**:
* [`Error`](https://github.com/emailr-dev/emailr-python/blob/master/./src/emailr/errors/error.py): Applicable to 44 of 64 methods.*
* [`BadRequestError`](https://github.com/emailr-dev/emailr-python/blob/master/./src/emailr/errors/badrequesterror.py): Invalid signature. Status code `400`. Applicable to 1 of 64 methods.*
* [`PostV1BillingCheckoutUnauthorizedError`](https://github.com/emailr-dev/emailr-python/blob/master/./src/emailr/errors/postv1billingcheckoutunauthorizederror.py): Unauthorized. Status code `401`. Applicable to 1 of 64 methods.*
* [`PostV1BillingPortalUnauthorizedError`](https://github.com/emailr-dev/emailr-python/blob/master/./src/emailr/errors/postv1billingportalunauthorizederror.py): Unauthorized. Status code `401`. Applicable to 1 of 64 methods.*
* [`GetV1BillingUsageUnauthorizedError`](https://github.com/emailr-dev/emailr-python/blob/master/./src/emailr/errors/getv1billingusageunauthorizederror.py): Unauthorized. Status code `401`. Applicable to 1 of 64 methods.*
* [`GetV1TopicsUnauthorizedError`](https://github.com/emailr-dev/emailr-python/blob/master/./src/emailr/errors/getv1topicsunauthorizederror.py): Unauthorized. Status code `401`. Applicable to 1 of 64 methods.*
* [`PostV1TopicsUnauthorizedError`](https://github.com/emailr-dev/emailr-python/blob/master/./src/emailr/errors/postv1topicsunauthorizederror.py): Unauthorized. Status code `401`. Applicable to 1 of 64 methods.*
* [`PutV1TopicsIDUnauthorizedError`](https://github.com/emailr-dev/emailr-python/blob/master/./src/emailr/errors/putv1topicsidunauthorizederror.py): Unauthorized. Status code `401`. Applicable to 1 of 64 methods.*
* [`DeleteV1TopicsIDUnauthorizedError`](https://github.com/emailr-dev/emailr-python/blob/master/./src/emailr/errors/deletev1topicsidunauthorizederror.py): Unauthorized. Status code `401`. Applicable to 1 of 64 methods.*
* [`PutV1TopicsIDNotFoundError`](https://github.com/emailr-dev/emailr-python/blob/master/./src/emailr/errors/putv1topicsidnotfounderror.py): Topic not found. Status code `404`. Applicable to 1 of 64 methods.*
* [`DeleteV1TopicsIDNotFoundError`](https://github.com/emailr-dev/emailr-python/blob/master/./src/emailr/errors/deletev1topicsidnotfounderror.py): Topic not found. Status code `404`. Applicable to 1 of 64 methods.*
* [`GetV1UnsubscribeOrganizationIDNotFoundError`](https://github.com/emailr-dev/emailr-python/blob/master/./src/emailr/errors/getv1unsubscribeorganizationidnotfounderror.py): Organization or contact not found. Status code `404`. Applicable to 1 of 64 methods.*
* [`PostV1UnsubscribeNotFoundError`](https://github.com/emailr-dev/emailr-python/blob/master/./src/emailr/errors/postv1unsubscribenotfounderror.py): Contact not found. Status code `404`. Applicable to 1 of 64 methods.*
* [`ResponseValidationError`](https://github.com/emailr-dev/emailr-python/blob/master/./src/emailr/errors/responsevalidationerror.py): Type mismatch between the response data and the expected Pydantic model. Provides access to the Pydantic validation error via the `cause` attribute.

</details>

\* Check [the method documentation](https://github.com/emailr-dev/emailr-python/blob/master/#available-resources-and-operations) to see if the error is applicable.
<!-- End Error Handling [errors] -->

<!-- Start Server Selection [server] -->
## Server Selection

### Override Server URL Per-Client

The default server can be overridden globally by passing a URL to the `server_url: str` optional parameter when initializing the SDK client instance. For example:
```python
from emailr import Emailr
import os


with Emailr(
    server_url="https://api.emailr.dev",
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.emails.send(request={
        "from_": "sender@example.com",
        "to": "recipient@example.com",
        "subject": "Hello World",
        "html": "<h1>Hello</h1>",
        "text": "Hello",
        "template_id": "123e4567-e89b-12d3-a456-426614174000",
        "template_data": {
            "name": "John",
            "company": "Acme",
        },
        "tags": {
            "campaign": "welcome",
            "source": "signup",
        },
        "attachments": [
            {
                "filename": "document.pdf",
                "content": "JVBERi0xLjQKJe...",
                "content_type": "application/pdf",
            },
        ],
        "reply_to": {
            "in_reply_to": "<message-id@domain.com>",
            "thread_id": "123e4567-e89b-12d3-a456-426614174000",
            "parent_email_id": "123e4567-e89b-12d3-a456-426614174000",
        },
        "reply_to_email": "support@example.com",
        "preview_text": "Check out our latest updates...",
    })

    # Handle response
    print(res)

```
<!-- End Server Selection [server] -->

<!-- Start Custom HTTP Client [http-client] -->
## Custom HTTP Client

The Python SDK makes API calls using the [httpx](https://www.python-httpx.org/) HTTP library.  In order to provide a convenient way to configure timeouts, cookies, proxies, custom headers, and other low-level configuration, you can initialize the SDK client with your own HTTP client instance.
Depending on whether you are using the sync or async version of the SDK, you can pass an instance of `HttpClient` or `AsyncHttpClient` respectively, which are Protocol's ensuring that the client has the necessary methods to make API calls.
This allows you to wrap the client with your own custom logic, such as adding custom headers, logging, or error handling, or you can just pass an instance of `httpx.Client` or `httpx.AsyncClient` directly.

For example, you could specify a header for every request that this sdk makes as follows:
```python
from emailr import Emailr
import httpx

http_client = httpx.Client(headers={"x-custom-header": "someValue"})
s = Emailr(client=http_client)
```

or you could wrap the client with your own custom logic:
```python
from emailr import Emailr
from emailr.httpclient import AsyncHttpClient
import httpx

class CustomClient(AsyncHttpClient):
    client: AsyncHttpClient

    def __init__(self, client: AsyncHttpClient):
        self.client = client

    async def send(
        self,
        request: httpx.Request,
        *,
        stream: bool = False,
        auth: Union[
            httpx._types.AuthTypes, httpx._client.UseClientDefault, None
        ] = httpx.USE_CLIENT_DEFAULT,
        follow_redirects: Union[
            bool, httpx._client.UseClientDefault
        ] = httpx.USE_CLIENT_DEFAULT,
    ) -> httpx.Response:
        request.headers["Client-Level-Header"] = "added by client"

        return await self.client.send(
            request, stream=stream, auth=auth, follow_redirects=follow_redirects
        )

    def build_request(
        self,
        method: str,
        url: httpx._types.URLTypes,
        *,
        content: Optional[httpx._types.RequestContent] = None,
        data: Optional[httpx._types.RequestData] = None,
        files: Optional[httpx._types.RequestFiles] = None,
        json: Optional[Any] = None,
        params: Optional[httpx._types.QueryParamTypes] = None,
        headers: Optional[httpx._types.HeaderTypes] = None,
        cookies: Optional[httpx._types.CookieTypes] = None,
        timeout: Union[
            httpx._types.TimeoutTypes, httpx._client.UseClientDefault
        ] = httpx.USE_CLIENT_DEFAULT,
        extensions: Optional[httpx._types.RequestExtensions] = None,
    ) -> httpx.Request:
        return self.client.build_request(
            method,
            url,
            content=content,
            data=data,
            files=files,
            json=json,
            params=params,
            headers=headers,
            cookies=cookies,
            timeout=timeout,
            extensions=extensions,
        )

s = Emailr(async_client=CustomClient(httpx.AsyncClient()))
```
<!-- End Custom HTTP Client [http-client] -->

<!-- Start Resource Management [resource-management] -->
## Resource Management

The `Emailr` class implements the context manager protocol and registers a finalizer function to close the underlying sync and async HTTPX clients it uses under the hood. This will close HTTP connections, release memory and free up other resources held by the SDK. In short-lived Python programs and notebooks that make a few SDK method calls, resource management may not be a concern. However, in longer-lived programs, it is beneficial to create a single SDK instance via a [context manager][context-manager] and reuse it across the application.

[context-manager]: https://docs.python.org/3/reference/datamodel.html#context-managers

```python
from emailr import Emailr
import os
def main():

    with Emailr(
        bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
    ) as e_client:
        # Rest of application here...


# Or when using async:
async def amain():

    async with Emailr(
        bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
    ) as e_client:
        # Rest of application here...
```
<!-- End Resource Management [resource-management] -->

<!-- Start Debugging [debug] -->
## Debugging

You can setup your SDK to emit debug logs for SDK requests and responses.

You can pass your own logger class directly into your SDK.
```python
from emailr import Emailr
import logging

logging.basicConfig(level=logging.DEBUG)
s = Emailr(debug_logger=logging.getLogger("emailr"))
```

You can also enable a default debug logger by setting an environment variable `EMAILR_DEBUG` to true.
<!-- End Debugging [debug] -->

<!-- Placeholder for Future Speakeasy SDK Sections -->

# Development

## Maturity

This SDK is in beta, and there may be breaking changes between versions without a major version update. Therefore, we recommend pinning usage
to a specific package version. This way, you can install the same version each time without breaking changes unless you are intentionally
looking for the latest version.

## Contributions

While we value open-source contributions to this SDK, this library is generated programmatically. Any manual changes added to internal files will be overwritten on the next generation. 
We look forward to hearing your feedback. Feel free to open a PR or an issue with a proof of concept and we'll do our best to include it in a future release. 

### SDK Created by [Speakeasy](https://www.speakeasy.com/?utm_source=emailr&utm_campaign=python)
