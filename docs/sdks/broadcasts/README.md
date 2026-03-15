# Broadcasts

## Overview

Broadcast campaign management

### Available Operations

* [create](#create) - Create broadcast
* [list](#list) - List broadcasts
* [send](#send) - Send broadcast
* [update_broadcast](#update_broadcast) - Update broadcast
* [get](#get) - Get broadcast
* [delete_broadcast](#delete_broadcast) - Delete broadcast

## create

Create a new email broadcast campaign

### Example Usage

<!-- UsageSnippet language="python" operationID="createBroadcast" method="post" path="/v1/broadcasts" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.broadcasts.create(request={
        "name": "Newsletter - January 2024",
        "subject": "Your monthly update",
        "from_email": "newsletter@example.com",
        "from_name": "Acme Newsletter",
        "reply_to": "reply@example.com",
        "preview_text": "Check out our latest updates...",
        "topic_id": "123e4567-e89b-12d3-a456-426614174000",
        "inbox_id": "123e4567-e89b-12d3-a456-426614174000",
        "inbox_ids": [
            "123e4567-e89b-12d3-a456-426614174000",
            "223e4567-e89b-12d3-a456-426614174001",
        ],
        "sending_speed": "auto",
        "tags": [
            "newsletter",
            "vip",
        ],
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                               | Type                                                                    | Required                                                                | Description                                                             |
| ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| `request`                                                               | [models.CreateBroadcastRequest](../../models/createbroadcastrequest.md) | :heavy_check_mark:                                                      | The request object to use for the request.                              |
| `retries`                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)        | :heavy_minus_sign:                                                      | Configuration to override the default retry behavior of the client.     |

### Response

**[models.Broadcast](../../models/broadcast.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 500                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## list

Get all broadcasts for your organization

### Example Usage

<!-- UsageSnippet language="python" operationID="listBroadcasts" method="get" path="/v1/broadcasts" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.broadcasts.list(tags="newsletter,vip")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `tags`                                                              | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | newsletter,vip                                                      |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[List[models.Broadcast]](../../models/.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 500                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## send

Send a broadcast to all recipients

### Example Usage

<!-- UsageSnippet language="python" operationID="sendBroadcast" method="post" path="/v1/broadcasts/{id}/send" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.broadcasts.send(id="123e4567-e89b-12d3-a456-426614174000")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 | 123e4567-e89b-12d3-a456-426614174000                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.SendBroadcastResponse](../../models/sendbroadcastresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 404                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## update_broadcast

Update a broadcast that has not been sent yet (draft or scheduled status only)

### Example Usage

<!-- UsageSnippet language="python" operationID="updateBroadcast" method="put" path="/v1/broadcasts/{id}" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.broadcasts.update_broadcast(id="123e4567-e89b-12d3-a456-426614174000", inbox_id="123e4567-e89b-12d3-a456-426614174000", tags=[
        "newsletter",
        "vip",
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                              | Type                                                                                                                                                                                   | Required                                                                                                                                                                               | Description                                                                                                                                                                            | Example                                                                                                                                                                                |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`                                                                                                                                                                                   | *str*                                                                                                                                                                                  | :heavy_check_mark:                                                                                                                                                                     | N/A                                                                                                                                                                                    | 123e4567-e89b-12d3-a456-426614174000                                                                                                                                                   |
| `name`                                                                                                                                                                                 | *Optional[str]*                                                                                                                                                                        | :heavy_minus_sign:                                                                                                                                                                     | N/A                                                                                                                                                                                    |                                                                                                                                                                                        |
| `subject`                                                                                                                                                                              | *Optional[str]*                                                                                                                                                                        | :heavy_minus_sign:                                                                                                                                                                     | N/A                                                                                                                                                                                    |                                                                                                                                                                                        |
| `from_email`                                                                                                                                                                           | *Optional[str]*                                                                                                                                                                        | :heavy_minus_sign:                                                                                                                                                                     | N/A                                                                                                                                                                                    |                                                                                                                                                                                        |
| `from_name`                                                                                                                                                                            | *Optional[str]*                                                                                                                                                                        | :heavy_minus_sign:                                                                                                                                                                     | N/A                                                                                                                                                                                    |                                                                                                                                                                                        |
| `reply_to`                                                                                                                                                                             | *OptionalNullable[str]*                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                     | N/A                                                                                                                                                                                    |                                                                                                                                                                                        |
| `preview_text`                                                                                                                                                                         | *OptionalNullable[str]*                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                     | N/A                                                                                                                                                                                    |                                                                                                                                                                                        |
| `template_id`                                                                                                                                                                          | *OptionalNullable[str]*                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                     | N/A                                                                                                                                                                                    |                                                                                                                                                                                        |
| `segment_id`                                                                                                                                                                           | *OptionalNullable[str]*                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                     | N/A                                                                                                                                                                                    |                                                                                                                                                                                        |
| `topic_id`                                                                                                                                                                             | *OptionalNullable[str]*                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                     | N/A                                                                                                                                                                                    |                                                                                                                                                                                        |
| `html_content`                                                                                                                                                                         | *Optional[str]*                                                                                                                                                                        | :heavy_minus_sign:                                                                                                                                                                     | N/A                                                                                                                                                                                    |                                                                                                                                                                                        |
| `text_content`                                                                                                                                                                         | *Optional[str]*                                                                                                                                                                        | :heavy_minus_sign:                                                                                                                                                                     | N/A                                                                                                                                                                                    |                                                                                                                                                                                        |
| `scheduled_at`                                                                                                                                                                         | [date](https://docs.python.org/3/library/datetime.html#date-objects)                                                                                                                   | :heavy_minus_sign:                                                                                                                                                                     | N/A                                                                                                                                                                                    |                                                                                                                                                                                        |
| `inbox_id`                                                                                                                                                                             | *OptionalNullable[str]*                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                     | Optional inbox ID. When provided, the inbox's name, from address, and reply-to address are used as defaults unless explicit values are given. Set to null to remove inbox association. | 123e4567-e89b-12d3-a456-426614174000                                                                                                                                                   |
| `inbox_ids`                                                                                                                                                                            | List[*str*]                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                     | Optional array of inbox IDs for inbox rotation. Set to null or empty to disable rotation.                                                                                              |                                                                                                                                                                                        |
| `sending_speed`                                                                                                                                                                        | [OptionalNullable[models.UpdateBroadcastRequestSendingSpeed]](../../models/updatebroadcastrequestsendingspeed.md)                                                                      | :heavy_minus_sign:                                                                                                                                                                     | Controls how fast emails are sent.                                                                                                                                                     |                                                                                                                                                                                        |
| `tags`                                                                                                                                                                                 | List[*str*]                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                     | Tags for categorization. Lowercase, max 50 chars each, max 20 tags.                                                                                                                    | [<br/>"newsletter",<br/>"vip"<br/>]                                                                                                                                                    |
| `retries`                                                                                                                                                                              | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                     | Configuration to override the default retry behavior of the client.                                                                                                                    |                                                                                                                                                                                        |

### Response

**[models.Broadcast](../../models/broadcast.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 400, 404                  | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## get

Get a specific broadcast by ID

### Example Usage

<!-- UsageSnippet language="python" operationID="getBroadcast" method="get" path="/v1/broadcasts/{id}" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.broadcasts.get(id="123e4567-e89b-12d3-a456-426614174000")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 | 123e4567-e89b-12d3-a456-426614174000                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.Broadcast](../../models/broadcast.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 404                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## delete_broadcast

Delete a broadcast. Only draft or scheduled broadcasts can be deleted.

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteBroadcast" method="delete" path="/v1/broadcasts/{id}" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.broadcasts.delete_broadcast(id="123e4567-e89b-12d3-a456-426614174000")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 | 123e4567-e89b-12d3-a456-426614174000                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.DeleteBroadcastResponse](../../models/deletebroadcastresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 400, 404                  | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |