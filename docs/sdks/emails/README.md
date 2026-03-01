# Emails

## Overview

Email sending and management

### Available Operations

* [send](#send) - Send an email
* [get](#get) - Get email by ID
* [list](#list) - List emails
* [forward_email](#forward_email) - Forward an email

## send

Send an email to one or multiple recipients

### Example Usage

<!-- UsageSnippet language="python" operationID="sendEmail" method="post" path="/v1/emails/send" -->
```python
from emailr import Emailr
from emailr.utils import parse_datetime
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.emails.send(request={
        "from_": "sender@example.com",
        "to": "recipient@example.com",
        "cc": [
            "cc1@example.com",
            "cc2@example.com",
        ],
        "bcc": [
            "bcc1@example.com",
            "bcc2@example.com",
        ],
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
        "scheduled_at": parse_datetime("2024-01-15T10:30:00Z"),
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `request`                                                           | [models.SendEmailRequest](../../models/sendemailrequest.md)         | :heavy_check_mark:                                                  | The request object to use for the request.                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.SendEmailResponse](../../models/sendemailresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 400, 401, 429             | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## get

Retrieve details of a specific email

### Example Usage

<!-- UsageSnippet language="python" operationID="getEmail" method="get" path="/v1/emails/{id}" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.emails.get(id="123e4567-e89b-12d3-a456-426614174000")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 | 123e4567-e89b-12d3-a456-426614174000                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.Email](../../models/email.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 401, 404                  | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## list

Get a paginated list of sent emails

### Example Usage

<!-- UsageSnippet language="python" operationID="listEmails" method="get" path="/v1/emails" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.emails.list(page="1", limit="50")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `page`                                                              | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | 1                                                                   |
| `limit`                                                             | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | 50                                                                  |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.ListEmailsResponse](../../models/listemailsresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 401                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## forward_email

Forward a received email to other recipients

### Example Usage

<!-- UsageSnippet language="python" operationID="forwardEmail" method="post" path="/v1/emails/forward" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.emails.forward_email()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `request`                                                           | [models.ForwardEmailRequest](../../models/forwardemailrequest.md)   | :heavy_check_mark:                                                  | The request object to use for the request.                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.SendEmailResponse](../../models/sendemailresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 404                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |