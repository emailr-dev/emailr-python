# ForwardingRules

## Overview

### Available Operations

* [create_forwarding_rule](#create_forwarding_rule) - Create forwarding rule
* [list_forwarding_rules](#list_forwarding_rules) - List forwarding rules
* [delete_forwarding_rule](#delete_forwarding_rule) - Delete forwarding rule

## create_forwarding_rule

Create an automated email forwarding rule

### Example Usage

<!-- UsageSnippet language="python" operationID="createForwardingRule" method="post" path="/v1/forwarding-rules" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.forwarding_rules.create_forwarding_rule()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                         | Type                                                                              | Required                                                                          | Description                                                                       |
| --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| `request`                                                                         | [models.CreateForwardingRuleRequest](../../models/createforwardingrulerequest.md) | :heavy_check_mark:                                                                | The request object to use for the request.                                        |
| `retries`                                                                         | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                  | :heavy_minus_sign:                                                                | Configuration to override the default retry behavior of the client.               |

### Response

**[models.CreateForwardingRuleResponse](../../models/createforwardingruleresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 400, 401                  | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## list_forwarding_rules

Get all forwarding rules for the organization

### Example Usage

<!-- UsageSnippet language="python" operationID="listForwardingRules" method="get" path="/v1/forwarding-rules" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.forwarding_rules.list_forwarding_rules()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.ListForwardingRulesResponse](../../models/listforwardingrulesresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 401                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## delete_forwarding_rule

Delete a forwarding rule by ID

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteForwardingRule" method="delete" path="/v1/forwarding-rules/{id}" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.forwarding_rules.delete_forwarding_rule(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DeleteForwardingRuleResponse](../../models/deleteforwardingruleresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 401, 404                  | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |