# Unsubscribe

## Overview

Email unsubscribe management

### Available Operations

* [get_v1_unsubscribe_organization_id_](#get_v1_unsubscribe_organization_id_)
* [post_v1_unsubscribe](#post_v1_unsubscribe)

## get_v1_unsubscribe_organization_id_

### Example Usage

<!-- UsageSnippet language="python" operationID="get_/v1/unsubscribe/{organizationId}" method="get" path="/v1/unsubscribe/{organizationId}" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.unsubscribe.get_v1_unsubscribe_organization_id_(organization_id="bef6eb39-8d8c-4d34-96dd-af6750d8a1a8", email="Jaylon.Watsica@yahoo.com")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `organization_id`                                                   | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `email`                                                             | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.GetV1UnsubscribeOrganizationIDResponse](../../models/getv1unsubscribeorganizationidresponse.md)**

### Errors

| Error Type                                         | Status Code                                        | Content Type                                       |
| -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- |
| errors.GetV1UnsubscribeOrganizationIDNotFoundError | 404                                                | application/json                                   |
| errors.EmailrDefaultError                          | 4XX, 5XX                                           | \*/\*                                              |

## post_v1_unsubscribe

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/v1/unsubscribe" method="post" path="/v1/unsubscribe" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.unsubscribe.post_v1_unsubscribe()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                   | Type                                                                        | Required                                                                    | Description                                                                 |
| --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| `request`                                                                   | [models.PostV1UnsubscribeRequest](../../models/postv1unsubscriberequest.md) | :heavy_check_mark:                                                          | The request object to use for the request.                                  |
| `retries`                                                                   | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)            | :heavy_minus_sign:                                                          | Configuration to override the default retry behavior of the client.         |

### Response

**[models.PostV1UnsubscribeResponse](../../models/postv1unsubscriberesponse.md)**

### Errors

| Error Type                            | Status Code                           | Content Type                          |
| ------------------------------------- | ------------------------------------- | ------------------------------------- |
| errors.PostV1UnsubscribeNotFoundError | 404                                   | application/json                      |
| errors.EmailrDefaultError             | 4XX, 5XX                              | \*/\*                                 |