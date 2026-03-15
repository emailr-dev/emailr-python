# Threads

## Overview

### Available Operations

* [list_threads](#list_threads) - List email threads
* [get_thread](#get_thread) - Get thread detail
* [update_email_labels](#update_email_labels) - Update email labels
* [update_thread_labels](#update_thread_labels) - Update thread labels
* [reply_to_thread](#reply_to_thread) - Reply to a thread
* [save_thread_draft](#save_thread_draft) - Save draft reply
* [get_thread_draft](#get_thread_draft) - Get draft reply
* [delete_thread_draft](#delete_thread_draft) - Delete draft reply

## list_threads

Get a paginated list of email threads filtered by label

### Example Usage

<!-- UsageSnippet language="python" operationID="listThreads" method="get" path="/v1/threads" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.threads.list_threads(label="inbox", page="1", limit="30", inbox_id="550e8400-e29b-41d4-a716-446655440000")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `label`                                                             | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | inbox                                                               |
| `page`                                                              | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |                                                                     |
| `limit`                                                             | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |                                                                     |
| `search`                                                            | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |                                                                     |
| `inbox_id`                                                          | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | 550e8400-e29b-41d4-a716-446655440000                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.ThreadListResponse](../../models/threadlistresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 401                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## get_thread

Get all messages in a thread

### Example Usage

<!-- UsageSnippet language="python" operationID="getThread" method="get" path="/v1/threads/{threadId}" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.threads.get_thread(thread_id="a3031242-915b-4575-bec5-8708aa45c2d6")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `thread_id`                                                         | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.ThreadDetail](../../models/threaddetail.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 401, 404                  | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## update_email_labels

Add or remove labels from an email

### Example Usage

<!-- UsageSnippet language="python" operationID="updateEmailLabels" method="patch" path="/v1/threads/emails/{emailId}/labels" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.threads.update_email_labels(email_id="bb51980c-6967-467c-9987-7393ef80bd00", add=[
        "starred",
    ], remove=[
        "unread",
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `email_id`                                                          | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |                                                                     |
| `add`                                                               | List[*str*]                                                         | :heavy_minus_sign:                                                  | N/A                                                                 | [<br/>"starred"<br/>]                                               |
| `remove`                                                            | List[*str*]                                                         | :heavy_minus_sign:                                                  | N/A                                                                 | [<br/>"unread"<br/>]                                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.UpdateEmailLabelsResponse](../../models/updateemaillabelsresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 401, 404                  | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## update_thread_labels

Add or remove labels from all emails in a thread

### Example Usage

<!-- UsageSnippet language="python" operationID="updateThreadLabels" method="patch" path="/v1/threads/{threadId}/labels" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.threads.update_thread_labels(thread_id="175b08b5-c0db-4378-b9f9-a88b9a5163da", add=[
        "starred",
    ], remove=[
        "unread",
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `thread_id`                                                         | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |                                                                     |
| `add`                                                               | List[*str*]                                                         | :heavy_minus_sign:                                                  | N/A                                                                 | [<br/>"starred"<br/>]                                               |
| `remove`                                                            | List[*str*]                                                         | :heavy_minus_sign:                                                  | N/A                                                                 | [<br/>"unread"<br/>]                                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.UpdateThreadLabelsResponse](../../models/updatethreadlabelsresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 401                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## reply_to_thread

Send a reply to a thread. From, from_name, reply_to, to, and subject are auto-resolved from the thread's inbox if not provided.

### Example Usage

<!-- UsageSnippet language="python" operationID="replyToThread" method="post" path="/v1/threads/{threadId}/reply" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.threads.reply_to_thread(thread_id="bf8dc90b-5d91-4545-acaa-3e528c0d803d", html="<p>Thanks for reaching out!</p>", text="Thanks for reaching out!")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                 | Type                                                                                      | Required                                                                                  | Description                                                                               | Example                                                                                   |
| ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| `thread_id`                                                                               | *str*                                                                                     | :heavy_check_mark:                                                                        | N/A                                                                                       |                                                                                           |
| `html`                                                                                    | *Optional[str]*                                                                           | :heavy_minus_sign:                                                                        | N/A                                                                                       | <p>Thanks for reaching out!</p>                                                           |
| `text`                                                                                    | *Optional[str]*                                                                           | :heavy_minus_sign:                                                                        | N/A                                                                                       | Thanks for reaching out!                                                                  |
| `to`                                                                                      | [Optional[models.ThreadReplyRequestTo]](../../models/threadreplyrequestto.md)             | :heavy_minus_sign:                                                                        | Override recipient. Auto-resolved from last received message if omitted.                  |                                                                                           |
| `cc`                                                                                      | [Optional[models.ThreadReplyRequestCc]](../../models/threadreplyrequestcc.md)             | :heavy_minus_sign:                                                                        | N/A                                                                                       |                                                                                           |
| `bcc`                                                                                     | [Optional[models.ThreadReplyRequestBcc]](../../models/threadreplyrequestbcc.md)           | :heavy_minus_sign:                                                                        | N/A                                                                                       |                                                                                           |
| `from_`                                                                                   | *Optional[str]*                                                                           | :heavy_minus_sign:                                                                        | Override sender. Auto-resolved from thread inbox if omitted.                              |                                                                                           |
| `from_name`                                                                               | *Optional[str]*                                                                           | :heavy_minus_sign:                                                                        | Override sender display name. Auto-resolved from inbox name if omitted.                   |                                                                                           |
| `reply_to_email`                                                                          | *Optional[str]*                                                                           | :heavy_minus_sign:                                                                        | Override Reply-To. Auto-resolved from inbox inbound address if omitted.                   |                                                                                           |
| `attachments`                                                                             | List[[models.ThreadReplyRequestAttachment](../../models/threadreplyrequestattachment.md)] | :heavy_minus_sign:                                                                        | N/A                                                                                       |                                                                                           |
| `retries`                                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                          | :heavy_minus_sign:                                                                        | Configuration to override the default retry behavior of the client.                       |                                                                                           |

### Response

**[models.ThreadReplyResponse](../../models/threadreplyresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 400, 401, 404             | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## save_thread_draft

Save or update a draft reply for a thread

### Example Usage

<!-- UsageSnippet language="python" operationID="saveThreadDraft" method="put" path="/v1/threads/{threadId}/draft" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.threads.save_thread_draft(thread_id="850dc5a3-faca-429e-941d-736e33e755ef")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `thread_id`                                                         | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `html`                                                              | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `text`                                                              | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `to`                                                                | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `cc`                                                                | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `bcc`                                                               | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `from_`                                                             | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `from_name`                                                         | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `reply_to_email`                                                    | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.ThreadDraft](../../models/threaddraft.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 401                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## get_thread_draft

Get the saved draft reply for a thread

### Example Usage

<!-- UsageSnippet language="python" operationID="getThreadDraft" method="get" path="/v1/threads/{threadId}/draft" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.threads.get_thread_draft(thread_id="5c843057-ab13-4caf-a6a8-8924b140c312")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `thread_id`                                                         | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.ThreadDraft](../../models/threaddraft.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 401, 404                  | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## delete_thread_draft

Discard the saved draft reply for a thread

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteThreadDraft" method="delete" path="/v1/threads/{threadId}/draft" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.threads.delete_thread_draft(thread_id="961c450c-0c9e-4c7d-869a-ae14db6cf938")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `thread_id`                                                         | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DeleteThreadDraftResponse](../../models/deletethreaddraftresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 401, 404                  | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |