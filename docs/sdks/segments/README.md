# Segments

## Overview

Contact segmentation

### Available Operations

* [create](#create) - Create segment
* [list](#list) - List segments
* [update_segment](#update_segment) - Update segment
* [delete_segment](#delete_segment) - Delete segment
* [add_contact](#add_contact) - Add contact to segment
* [get_segment_contacts](#get_segment_contacts) - Get segment contacts
* [bulk_add_contacts_to_segment](#bulk_add_contacts_to_segment) - Bulk add contacts to segment

## create

Create a new contact segment. For data-driven segments, conditions must be provided.

### Example Usage

<!-- UsageSnippet language="python" operationID="createSegment" method="post" path="/v1/segments" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.segments.create(request={
        "name": "Active Users",
        "description": "Users who opened an email in the last 30 days",
        "type": "data_driven",
        "conditions": {
            "logic": "and",
            "rules": [
                {
                    "field": "properties.plan_type",
                    "operator": "equals",
                    "value": "premium",
                },
            ],
        },
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `request`                                                           | [models.CreateSegmentRequest](../../models/createsegmentrequest.md) | :heavy_check_mark:                                                  | The request object to use for the request.                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.Segment](../../models/segment.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 400                       | application/json          |
| errors.Error              | 500                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## list

Get all segments for your organization

### Example Usage

<!-- UsageSnippet language="python" operationID="listSegments" method="get" path="/v1/segments" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.segments.list()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[List[models.Segment]](../../models/.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 500                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## update_segment

Update an existing segment. Segment type cannot be changed after creation.

### Example Usage

<!-- UsageSnippet language="python" operationID="updateSegment" method="put" path="/v1/segments/{id}" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.segments.update_segment(id="123e4567-e89b-12d3-a456-426614174000", name="Active Users", description="Users who opened an email in the last 30 days", conditions={
        "logic": "and",
        "rules": [
            {
                "field": "properties.plan_type",
                "operator": "equals",
                "value": "premium",
            },
        ],
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                      | Type                                                                                                           | Required                                                                                                       | Description                                                                                                    | Example                                                                                                        |
| -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| `id`                                                                                                           | *str*                                                                                                          | :heavy_check_mark:                                                                                             | N/A                                                                                                            | 123e4567-e89b-12d3-a456-426614174000                                                                           |
| `name`                                                                                                         | *Optional[str]*                                                                                                | :heavy_minus_sign:                                                                                             | N/A                                                                                                            | Active Users                                                                                                   |
| `description`                                                                                                  | *Optional[str]*                                                                                                | :heavy_minus_sign:                                                                                             | N/A                                                                                                            | Users who opened an email in the last 30 days                                                                  |
| `conditions`                                                                                                   | [Optional[models.FilterConditions]](../../models/filterconditions.md)                                          | :heavy_minus_sign:                                                                                             | N/A                                                                                                            | {<br/>"logic": "and",<br/>"rules": [<br/>{<br/>"field": "properties.plan_type",<br/>"operator": "equals",<br/>"value": "premium"<br/>}<br/>]<br/>} |
| `retries`                                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                               | :heavy_minus_sign:                                                                                             | Configuration to override the default retry behavior of the client.                                            |                                                                                                                |

### Response

**[models.Segment](../../models/segment.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 400, 404                  | application/json          |
| errors.Error              | 500                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## delete_segment

Delete a segment. Contacts in the segment will not be deleted.

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteSegment" method="delete" path="/v1/segments/{id}" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.segments.delete_segment(id="123e4567-e89b-12d3-a456-426614174000")

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

## add_contact

Add a contact to a segment

### Example Usage

<!-- UsageSnippet language="python" operationID="addContactToSegment" method="post" path="/v1/segments/{id}/contacts/{contactId}" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.segments.add_contact(id="123e4567-e89b-12d3-a456-426614174000", contact_id="123e4567-e89b-12d3-a456-426614174000")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 | 123e4567-e89b-12d3-a456-426614174000                                |
| `contact_id`                                                        | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 | 123e4567-e89b-12d3-a456-426614174000                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.Success](../../models/success.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 500                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## get_segment_contacts

Get contacts in a segment. For manual segments, returns contacts from the contact_segments join table. For data-driven segments, evaluates filter conditions at query time.

### Example Usage

<!-- UsageSnippet language="python" operationID="getSegmentContacts" method="get" path="/v1/segments/{id}/contacts" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.segments.get_segment_contacts(id="123e4567-e89b-12d3-a456-426614174000", limit="100", offset="0")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 | 123e4567-e89b-12d3-a456-426614174000                                |
| `limit`                                                             | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | 100                                                                 |
| `offset`                                                            | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | 0                                                                   |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.SegmentContactsResponse](../../models/segmentcontactsresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 404                       | application/json          |
| errors.Error              | 500                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## bulk_add_contacts_to_segment

Add multiple contacts to a manual segment by contact IDs or email addresses. Data-driven segments do not support bulk add operations.

### Example Usage

<!-- UsageSnippet language="python" operationID="bulkAddContactsToSegment" method="post" path="/v1/segments/{id}/contacts/bulk" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.segments.bulk_add_contacts_to_segment(id="123e4567-e89b-12d3-a456-426614174000", contact_ids=[
        "123e4567-e89b-12d3-a456-426614174000",
        "223e4567-e89b-12d3-a456-426614174001",
    ], emails=[
        "user1@example.com",
        "user2@example.com",
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                          | Type                                                                               | Required                                                                           | Description                                                                        | Example                                                                            |
| ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| `id`                                                                               | *str*                                                                              | :heavy_check_mark:                                                                 | N/A                                                                                | 123e4567-e89b-12d3-a456-426614174000                                               |
| `contact_ids`                                                                      | List[*str*]                                                                        | :heavy_minus_sign:                                                                 | Array of contact IDs to add to the segment                                         | [<br/>"123e4567-e89b-12d3-a456-426614174000",<br/>"223e4567-e89b-12d3-a456-426614174001"<br/>] |
| `emails`                                                                           | List[*str*]                                                                        | :heavy_minus_sign:                                                                 | Array of email addresses to add to the segment (will be looked up in contacts)     | [<br/>"user1@example.com",<br/>"user2@example.com"<br/>]                           |
| `retries`                                                                          | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                   | :heavy_minus_sign:                                                                 | Configuration to override the default retry behavior of the client.                |                                                                                    |

### Response

**[models.BulkAddContactsToSegmentResponse](../../models/bulkaddcontactstosegmentresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 400, 404                  | application/json          |
| errors.Error              | 500                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |