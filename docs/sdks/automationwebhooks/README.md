# AutomationWebhooks

## Overview

### Available Operations

* [subscribe_automation_webhook](#subscribe_automation_webhook) - Subscribe automation webhook
* [unsubscribe_automation_webhook](#unsubscribe_automation_webhook) - Unsubscribe automation webhook
* [list_automation_webhooks](#list_automation_webhooks) - List automation webhooks
* [list_automation_inboxes](#list_automation_inboxes) - List inboxes
* [test_automation_webhook](#test_automation_webhook) - Send test event

## subscribe_automation_webhook

Register a webhook URL for a third-party automation (Zapier, n8n)

### Example Usage

<!-- UsageSnippet language="python" operationID="subscribeAutomationWebhook" method="post" path="/v1/automation-webhooks/subscribe" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.automation_webhooks.subscribe_automation_webhook(request={
        "target_url": "https://hooks.zapier.com/hooks/catch/123/abc",
        "event_type": "email.received",
        "provider": "zapier",
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                     | Type                                                                                          | Required                                                                                      | Description                                                                                   |
| --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| `request`                                                                                     | [models.SubscribeAutomationWebhookRequest](../../models/subscribeautomationwebhookrequest.md) | :heavy_check_mark:                                                                            | The request object to use for the request.                                                    |
| `retries`                                                                                     | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                              | :heavy_minus_sign:                                                                            | Configuration to override the default retry behavior of the client.                           |

### Response

**[models.AutomationWebhook](../../models/automationwebhook.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 500                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## unsubscribe_automation_webhook

Remove a webhook URL for a third-party automation

### Example Usage

<!-- UsageSnippet language="python" operationID="unsubscribeAutomationWebhook" method="delete" path="/v1/automation-webhooks/unsubscribe" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.automation_webhooks.unsubscribe_automation_webhook(request={
        "target_url": "https://hooks.zapier.com/hooks/catch/123/abc",
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                         | Type                                                                                              | Required                                                                                          | Description                                                                                       |
| ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| `request`                                                                                         | [models.UnsubscribeAutomationWebhookRequest](../../models/unsubscribeautomationwebhookrequest.md) | :heavy_check_mark:                                                                                | The request object to use for the request.                                                        |
| `retries`                                                                                         | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                  | :heavy_minus_sign:                                                                                | Configuration to override the default retry behavior of the client.                               |

### Response

**[models.Success](../../models/success.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 500                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## list_automation_webhooks

Get all automation webhooks for your organization

### Example Usage

<!-- UsageSnippet language="python" operationID="listAutomationWebhooks" method="get" path="/v1/automation-webhooks" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.automation_webhooks.list_automation_webhooks()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[List[models.AutomationWebhook]](../../models/.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 500                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## list_automation_inboxes

Get available inboxes for automation triggers (Zapier, n8n)

### Example Usage

<!-- UsageSnippet language="python" operationID="listAutomationInboxes" method="get" path="/v1/automation-webhooks/inboxes" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.automation_webhooks.list_automation_inboxes()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[List[models.ListAutomationInboxesResponse]](../../models/.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 500                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## test_automation_webhook

Send a sample email.received event to a webhook URL for testing

### Example Usage

<!-- UsageSnippet language="python" operationID="testAutomationWebhook" method="post" path="/v1/automation-webhooks/test" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.automation_webhooks.test_automation_webhook(request={
        "target_url": "https://hooks.zapier.com/hooks/catch/123/abc",
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                           | Type                                                                                | Required                                                                            | Description                                                                         |
| ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `request`                                                                           | [models.TestAutomationWebhookRequest](../../models/testautomationwebhookrequest.md) | :heavy_check_mark:                                                                  | The request object to use for the request.                                          |
| `retries`                                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                    | :heavy_minus_sign:                                                                  | Configuration to override the default retry behavior of the client.                 |

### Response

**[models.Success](../../models/success.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 500                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |