# Integrations

## Overview

OAuth integrations (Supabase, Vercel)

### Available Operations

* [get_v1_integrations_connections](#get_v1_integrations_connections)
* [get_v1_integrations_supabase_authorize](#get_v1_integrations_supabase_authorize)
* [get_v1_integrations_supabase_callback](#get_v1_integrations_supabase_callback)
* [delete_v1_integrations_id_](#delete_v1_integrations_id_)
* [get_v1_integrations_vercel_authorize](#get_v1_integrations_vercel_authorize)
* [get_v1_integrations_vercel_callback](#get_v1_integrations_vercel_callback)

## get_v1_integrations_connections

### Example Usage

<!-- UsageSnippet language="python" operationID="get_/v1/integrations/connections" method="get" path="/v1/integrations/connections" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.integrations.get_v1_integrations_connections()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.GetV1IntegrationsConnectionsResponse](../../models/getv1integrationsconnectionsresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## get_v1_integrations_supabase_authorize

### Example Usage

<!-- UsageSnippet language="python" operationID="get_/v1/integrations/supabase/authorize" method="get" path="/v1/integrations/supabase/authorize" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    e_client.integrations.get_v1_integrations_supabase_authorize()

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## get_v1_integrations_supabase_callback

### Example Usage

<!-- UsageSnippet language="python" operationID="get_/v1/integrations/supabase/callback" method="get" path="/v1/integrations/supabase/callback" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    e_client.integrations.get_v1_integrations_supabase_callback(code="<value>", state="Idaho")

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `code`                                                              | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `state`                                                             | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## delete_v1_integrations_id_

### Example Usage

<!-- UsageSnippet language="python" operationID="delete_/v1/integrations/{id}" method="delete" path="/v1/integrations/{id}" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.integrations.delete_v1_integrations_id_(id="c82e3660-bf8b-49a7-8779-7fc400a384d3")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DeleteV1IntegrationsIDResponse](../../models/deletev1integrationsidresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## get_v1_integrations_vercel_authorize

### Example Usage

<!-- UsageSnippet language="python" operationID="get_/v1/integrations/vercel/authorize" method="get" path="/v1/integrations/vercel/authorize" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    e_client.integrations.get_v1_integrations_vercel_authorize()

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## get_v1_integrations_vercel_callback

### Example Usage

<!-- UsageSnippet language="python" operationID="get_/v1/integrations/vercel/callback" method="get" path="/v1/integrations/vercel/callback" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    e_client.integrations.get_v1_integrations_vercel_callback(code="<value>", state="Illinois")

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `code`                                                              | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `state`                                                             | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |