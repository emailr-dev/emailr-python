# Billing

## Overview

Subscription billing and usage

### Available Operations

* [post_v1_billing_checkout](#post_v1_billing_checkout)
* [post_v1_billing_portal](#post_v1_billing_portal)
* [get_v1_billing_usage](#get_v1_billing_usage)
* [post_v1_billing_webhooks](#post_v1_billing_webhooks)

## post_v1_billing_checkout

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/v1/billing/checkout" method="post" path="/v1/billing/checkout" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.billing.post_v1_billing_checkout()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                           | Type                                                                                | Required                                                                            | Description                                                                         |
| ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `request`                                                                           | [models.PostV1BillingCheckoutRequest](../../models/postv1billingcheckoutrequest.md) | :heavy_check_mark:                                                                  | The request object to use for the request.                                          |
| `retries`                                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                    | :heavy_minus_sign:                                                                  | Configuration to override the default retry behavior of the client.                 |

### Response

**[models.PostV1BillingCheckoutResponse](../../models/postv1billingcheckoutresponse.md)**

### Errors

| Error Type                                    | Status Code                                   | Content Type                                  |
| --------------------------------------------- | --------------------------------------------- | --------------------------------------------- |
| errors.PostV1BillingCheckoutUnauthorizedError | 401                                           | application/json                              |
| errors.EmailrDefaultError                     | 4XX, 5XX                                      | \*/\*                                         |

## post_v1_billing_portal

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/v1/billing/portal" method="post" path="/v1/billing/portal" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.billing.post_v1_billing_portal()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.PostV1BillingPortalResponse](../../models/postv1billingportalresponse.md)**

### Errors

| Error Type                                  | Status Code                                 | Content Type                                |
| ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| errors.PostV1BillingPortalUnauthorizedError | 401                                         | application/json                            |
| errors.EmailrDefaultError                   | 4XX, 5XX                                    | \*/\*                                       |

## get_v1_billing_usage

### Example Usage

<!-- UsageSnippet language="python" operationID="get_/v1/billing/usage" method="get" path="/v1/billing/usage" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.billing.get_v1_billing_usage()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.GetV1BillingUsageResponse](../../models/getv1billingusageresponse.md)**

### Errors

| Error Type                                | Status Code                               | Content Type                              |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| errors.GetV1BillingUsageUnauthorizedError | 401                                       | application/json                          |
| errors.EmailrDefaultError                 | 4XX, 5XX                                  | \*/\*                                     |

## post_v1_billing_webhooks

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/v1/billing/webhooks" method="post" path="/v1/billing/webhooks" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.billing.post_v1_billing_webhooks()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `request`                                                           | [Any](../../models/.md)                                             | :heavy_check_mark:                                                  | The request object to use for the request.                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.PostV1BillingWebhooksResponse](../../models/postv1billingwebhooksresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.BadRequestError    | 400                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |