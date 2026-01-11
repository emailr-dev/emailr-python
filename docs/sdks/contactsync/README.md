# ContactSync

## Overview

Third-party contact synchronization

### Available Operations

* [post_v1_contact_sync_supabase](#post_v1_contact_sync_supabase)
* [post_v1_contact_sync_webhook_sync_id_](#post_v1_contact_sync_webhook_sync_id_)
* [get_v1_contact_sync](#get_v1_contact_sync)
* [delete_v1_contact_sync_id_](#delete_v1_contact_sync_id_)

## post_v1_contact_sync_supabase

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/v1/contact-sync/supabase" method="post" path="/v1/contact-sync/supabase" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.contact_sync.post_v1_contact_sync_supabase()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                   | Type                                                                                        | Required                                                                                    | Description                                                                                 |
| ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| `request`                                                                                   | [models.PostV1ContactSyncSupabaseRequest](../../models/postv1contactsyncsupabaserequest.md) | :heavy_check_mark:                                                                          | The request object to use for the request.                                                  |
| `retries`                                                                                   | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                            | :heavy_minus_sign:                                                                          | Configuration to override the default retry behavior of the client.                         |

### Response

**[models.PostV1ContactSyncSupabaseResponse](../../models/postv1contactsyncsupabaseresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## post_v1_contact_sync_webhook_sync_id_

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/v1/contact-sync/webhook/{syncId}" method="post" path="/v1/contact-sync/webhook/{syncId}" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.contact_sync.post_v1_contact_sync_webhook_sync_id_(sync_id="0e5a8223-01fb-4449-9a79-08b3e3bb4b0f")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `sync_id`                                                           | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `body`                                                              | *OptionalNullable[Any]*                                             | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.PostV1ContactSyncWebhookSyncIDResponse](../../models/postv1contactsyncwebhooksyncidresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## get_v1_contact_sync

### Example Usage

<!-- UsageSnippet language="python" operationID="get_/v1/contact-sync" method="get" path="/v1/contact-sync" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.contact_sync.get_v1_contact_sync()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.GetV1ContactSyncResponse](../../models/getv1contactsyncresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## delete_v1_contact_sync_id_

### Example Usage

<!-- UsageSnippet language="python" operationID="delete_/v1/contact-sync/{id}" method="delete" path="/v1/contact-sync/{id}" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.contact_sync.delete_v1_contact_sync_id_(id="799be7ce-fc7e-4d43-9d6b-3b6334c08b6d")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DeleteV1ContactSyncIDResponse](../../models/deletev1contactsyncidresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |