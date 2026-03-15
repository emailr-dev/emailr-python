# Inboxes

## Overview

### Available Operations

* [create_inbox](#create_inbox) - Create inbox
* [list_inboxes](#list_inboxes) - List inboxes
* [get_inbox](#get_inbox) - Get inbox
* [update_inbox](#update_inbox) - Update inbox
* [delete_inbox](#delete_inbox) - Delete inbox

## create_inbox

Create a new inbox for the organization

### Example Usage

<!-- UsageSnippet language="python" operationID="createInbox" method="post" path="/v1/inboxes" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.inboxes.create_inbox(request={
        "name": "Support",
        "username": "support",
        "domain": "example.com",
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `request`                                                           | [models.CreateInboxRequest](../../models/createinboxrequest.md)     | :heavy_check_mark:                                                  | The request object to use for the request.                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.Inbox](../../models/inbox.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 400, 409                  | application/json          |
| errors.Error              | 500                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## list_inboxes

Get all inboxes for the authenticated organization

### Example Usage

<!-- UsageSnippet language="python" operationID="listInboxes" method="get" path="/v1/inboxes" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.inboxes.list_inboxes()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[List[models.Inbox]](../../models/.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 500                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## get_inbox

Get a specific inbox by ID

### Example Usage

<!-- UsageSnippet language="python" operationID="getInbox" method="get" path="/v1/inboxes/{id}" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.inboxes.get_inbox(id="123e4567-e89b-12d3-a456-426614174000")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 | 123e4567-e89b-12d3-a456-426614174000                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.Inbox](../../models/inbox.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 404                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## update_inbox

Update an inbox's display name (username and domain are immutable)

### Example Usage

<!-- UsageSnippet language="python" operationID="updateInbox" method="put" path="/v1/inboxes/{id}" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.inboxes.update_inbox(id="123e4567-e89b-12d3-a456-426614174000", name="Support Team")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 | 123e4567-e89b-12d3-a456-426614174000                                |
| `name`                                                              | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | Support Team                                                        |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.Inbox](../../models/inbox.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 404                       | application/json          |
| errors.Error              | 500                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## delete_inbox

Delete an inbox. References in emails, templates, and broadcasts will be set to null.

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteInbox" method="delete" path="/v1/inboxes/{id}" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.inboxes.delete_inbox(id="123e4567-e89b-12d3-a456-426614174000")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 | 123e4567-e89b-12d3-a456-426614174000                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.Success](../../models/success.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 404                       | application/json          |
| errors.Error              | 500                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |