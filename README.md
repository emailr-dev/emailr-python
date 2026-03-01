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
* [emailr](#emailr)
  * [SDK Installation](#sdk-installation)
  * [IDE Support](#ide-support)
  * [SDK Example Usage](#sdk-example-usage)
  * [Authentication](#authentication)
  * [Available Resources and Operations](#available-resources-and-operations)
  * [Retries](#retries)
  * [Error Handling](#error-handling)
  * [Server Selection](#server-selection)
  * [Custom HTTP Client](#custom-http-client)
  * [Resource Management](#resource-management)
  * [Debugging](#debugging)
* [Development](#development)
  * [Maturity](#maturity)
  * [Contributions](#contributions)

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
# requires-python = ">=3.10"
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

    res = e_client.templates.get_template_preview(template_id="123e4567-e89b-12d3-a456-426614174000")

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

        res = await e_client.templates.get_template_preview_async(template_id="123e4567-e89b-12d3-a456-426614174000")

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

    res = e_client.templates.get_template_preview(template_id="123e4567-e89b-12d3-a456-426614174000")

    # Handle response
    print(res)

```
<!-- End Authentication [security] -->

<!-- Start Available Resources and Operations [operations] -->
## Available Resources and Operations

<details open>
<summary>Available methods</summary>

### [Broadcasts](docs/sdks/broadcasts/README.md)

* [create](docs/sdks/broadcasts/README.md#create) - Create broadcast
* [list](docs/sdks/broadcasts/README.md#list) - List broadcasts
* [send](docs/sdks/broadcasts/README.md#send) - Send broadcast
* [get](docs/sdks/broadcasts/README.md#get) - Get broadcast

### [ContactProperties](docs/sdks/contactproperties/README.md)

* [create_property_definition](docs/sdks/contactproperties/README.md#create_property_definition) - Create property definition
* [list_property_definitions](docs/sdks/contactproperties/README.md#list_property_definitions) - List property definitions
* [delete_property_definition](docs/sdks/contactproperties/README.md#delete_property_definition) - Delete property definition

### [Contacts](docs/sdks/contacts/README.md)

* [create](docs/sdks/contacts/README.md#create) - Create a contact
* [list](docs/sdks/contacts/README.md#list) - List contacts
* [bulk_create](docs/sdks/contacts/README.md#bulk_create) - Bulk create contacts
* [get_contact_limit](docs/sdks/contacts/README.md#get_contact_limit) - Get contact limit info
* [get](docs/sdks/contacts/README.md#get) - Get contact
* [update](docs/sdks/contacts/README.md#update) - Update contact
* [delete](docs/sdks/contacts/README.md#delete) - Delete contact

### [Domains](docs/sdks/domains/README.md)

* [add](docs/sdks/domains/README.md#add) - Add domain
* [list](docs/sdks/domains/README.md#list) - List domains
* [verify](docs/sdks/domains/README.md#verify) - Verify domain
* [get_dns_status](docs/sdks/domains/README.md#get_dns_status) - Get DNS status
* [get_domain](docs/sdks/domains/README.md#get_domain) - Get domain
* [update](docs/sdks/domains/README.md#update) - Update domain
* [delete](docs/sdks/domains/README.md#delete) - Delete domain

### [Emails](docs/sdks/emails/README.md)

* [send](docs/sdks/emails/README.md#send) - Send an email
* [get](docs/sdks/emails/README.md#get) - Get email by ID
* [list](docs/sdks/emails/README.md#list) - List emails
* [forward_email](docs/sdks/emails/README.md#forward_email) - Forward an email

### [ForwardingRules](docs/sdks/forwardingrules/README.md)

* [create_forwarding_rule](docs/sdks/forwardingrules/README.md#create_forwarding_rule) - Create forwarding rule
* [list_forwarding_rules](docs/sdks/forwardingrules/README.md#list_forwarding_rules) - List forwarding rules
* [delete_forwarding_rule](docs/sdks/forwardingrules/README.md#delete_forwarding_rule) - Delete forwarding rule

### [Import](docs/sdks/import/README.md)

* [csv_import_preview](docs/sdks/import/README.md#csv_import_preview) - Preview CSV import
* [csv_import](docs/sdks/import/README.md#csv_import) - Import contacts from CSV

### [Invitations](docs/sdks/invitations/README.md)

* [create_invitation](docs/sdks/invitations/README.md#create_invitation) - Create team invitation
* [list_invitations](docs/sdks/invitations/README.md#list_invitations) - List pending invitations
* [cancel_invitation](docs/sdks/invitations/README.md#cancel_invitation) - Cancel invitation
* [get_invitation_details](docs/sdks/invitations/README.md#get_invitation_details) - Get invitation details (public)
* [accept_invitation](docs/sdks/invitations/README.md#accept_invitation) - Accept invitation

### [Segments](docs/sdks/segments/README.md)

* [create](docs/sdks/segments/README.md#create) - Create segment
* [list](docs/sdks/segments/README.md#list) - List segments
* [update_segment](docs/sdks/segments/README.md#update_segment) - Update segment
* [delete_segment](docs/sdks/segments/README.md#delete_segment) - Delete segment
* [add_contact](docs/sdks/segments/README.md#add_contact) - Add contact to segment
* [get_segment_contacts](docs/sdks/segments/README.md#get_segment_contacts) - Get segment contacts
* [bulk_add_contacts_to_segment](docs/sdks/segments/README.md#bulk_add_contacts_to_segment) - Bulk add contacts to segment

### [Templates](docs/sdks/templates/README.md)

* [get_template_preview](docs/sdks/templates/README.md#get_template_preview) - Get template preview (public)
* [create](docs/sdks/templates/README.md#create) - Create a template
* [list](docs/sdks/templates/README.md#list) - List templates
* [get](docs/sdks/templates/README.md#get) - Get template
* [update](docs/sdks/templates/README.md#update) - Update template
* [delete](docs/sdks/templates/README.md#delete) - Delete template
* [update_template_preview](docs/sdks/templates/README.md#update_template_preview) - Update template preview
* [publish_template](docs/sdks/templates/README.md#publish_template) - Publish template

### [Webhooks](docs/sdks/webhooks/README.md)

* [create](docs/sdks/webhooks/README.md#create) - Create webhook
* [list](docs/sdks/webhooks/README.md#list) - List webhooks
* [toggle](docs/sdks/webhooks/README.md#toggle) - Toggle webhook
* [delete](docs/sdks/webhooks/README.md#delete) - Delete webhook
* [list_deliveries](docs/sdks/webhooks/README.md#list_deliveries) - Get webhook deliveries

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

    res = e_client.templates.get_template_preview(template_id="123e4567-e89b-12d3-a456-426614174000",
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

    res = e_client.templates.get_template_preview(template_id="123e4567-e89b-12d3-a456-426614174000")

    # Handle response
    print(res)

```
<!-- End Retries [retries] -->

<!-- Start Error Handling [errors] -->
## Error Handling

[`EmailrError`](./src/emailr/errors/emailrerror.py) is the base class for all HTTP error responses. It has the following properties:

| Property           | Type             | Description                                                                             |
| ------------------ | ---------------- | --------------------------------------------------------------------------------------- |
| `err.message`      | `str`            | Error message                                                                           |
| `err.status_code`  | `int`            | HTTP response status code eg `404`                                                      |
| `err.headers`      | `httpx.Headers`  | HTTP response headers                                                                   |
| `err.body`         | `str`            | HTTP body. Can be empty string if no body is returned.                                  |
| `err.raw_response` | `httpx.Response` | Raw HTTP response                                                                       |
| `err.data`         |                  | Optional. Some errors may contain structured data. [See Error Classes](#error-classes). |

### Example
```python
from emailr import Emailr, errors
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:
    res = None
    try:

        res = e_client.templates.get_template_preview(template_id="123e4567-e89b-12d3-a456-426614174000")

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
        if isinstance(e, errors.NotFoundError):
            print(e.data.error)  # str
            print(e.data.code)  # str
```

### Error Classes
**Primary errors:**
* [`EmailrError`](./src/emailr/errors/emailrerror.py): The base class for HTTP error responses.
  * [`Error`](./src/emailr/errors/error.py): *

<details><summary>Less common errors (6)</summary>

<br />

**Network errors:**
* [`httpx.RequestError`](https://www.python-httpx.org/exceptions/#httpx.RequestError): Base class for request errors.
    * [`httpx.ConnectError`](https://www.python-httpx.org/exceptions/#httpx.ConnectError): HTTP client was unable to make a request to a server.
    * [`httpx.TimeoutException`](https://www.python-httpx.org/exceptions/#httpx.TimeoutException): HTTP request timed out.


**Inherit from [`EmailrError`](./src/emailr/errors/emailrerror.py)**:
* [`NotFoundError`](./src/emailr/errors/notfounderror.py): Template not found or no preview exists. Status code `404`. Applicable to 1 of 55 methods.*
* [`ResponseValidationError`](./src/emailr/errors/responsevalidationerror.py): Type mismatch between the response data and the expected Pydantic model. Provides access to the Pydantic validation error via the `cause` attribute.

</details>

\* Check [the method documentation](#available-resources-and-operations) to see if the error is applicable.
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

    res = e_client.templates.get_template_preview(template_id="123e4567-e89b-12d3-a456-426614174000")

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
