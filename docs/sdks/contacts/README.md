# Contacts

## Overview

Contact management

### Available Operations

* [create](#create) - Create a contact
* [list](#list) - List contacts
* [bulk_create](#bulk_create) - Bulk create contacts
* [get_contact_limit](#get_contact_limit) - Get contact limit info
* [get](#get) - Get contact
* [update](#update) - Update contact
* [delete](#delete) - Delete contact

## create

Create a new contact in your organization

### Example Usage

<!-- UsageSnippet language="python" operationID="createContact" method="post" path="/v1/contacts" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.contacts.create(request={
        "email": "contact@example.com",
        "first_name": "John",
        "last_name": "Doe",
        "metadata": {
            "source": "website",
            "plan": "pro",
        },
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `request`                                                           | [models.CreateContactRequest](../../models/createcontactrequest.md) | :heavy_check_mark:                                                  | The request object to use for the request.                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.Contact](../../models/contact.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 400, 401                  | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## list

Get a list of contacts with optional filtering

### Example Usage

<!-- UsageSnippet language="python" operationID="listContacts" method="get" path="/v1/contacts" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.contacts.list(limit="100", offset="0", subscribed="true")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `limit`                                                             | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | 100                                                                 |
| `offset`                                                            | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | 0                                                                   |
| `subscribed`                                                        | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | true                                                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.ContactListResponse](../../models/contactlistresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 401                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## bulk_create

Import multiple contacts at once

### Example Usage

<!-- UsageSnippet language="python" operationID="bulkCreateContacts" method="post" path="/v1/contacts/bulk" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.contacts.bulk_create(request={
        "contacts": [],
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                     | Type                                                                          | Required                                                                      | Description                                                                   |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `request`                                                                     | [models.BulkCreateContactsRequest](../../models/bulkcreatecontactsrequest.md) | :heavy_check_mark:                                                            | The request object to use for the request.                                    |
| `retries`                                                                     | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)              | :heavy_minus_sign:                                                            | Configuration to override the default retry behavior of the client.           |

### Response

**[models.BulkCreateContactsResponse](../../models/bulkcreatecontactsresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 401                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## get_contact_limit

Get the organization's contact limit, current count, and remaining available slots

### Example Usage

<!-- UsageSnippet language="python" operationID="getContactLimit" method="get" path="/v1/contacts/limit" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.contacts.get_contact_limit()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.GetContactLimitResponse](../../models/getcontactlimitresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 401                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## get

Get a specific contact by ID

### Example Usage

<!-- UsageSnippet language="python" operationID="getContact" method="get" path="/v1/contacts/{id}" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.contacts.get(id="123e4567-e89b-12d3-a456-426614174000")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 | 123e4567-e89b-12d3-a456-426614174000                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.Contact](../../models/contact.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 401, 404                  | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## update

Update a contact's information

### Example Usage

<!-- UsageSnippet language="python" operationID="updateContact" method="put" path="/v1/contacts/{id}" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.contacts.update(id="123e4567-e89b-12d3-a456-426614174000", email="contact@example.com", first_name="John", last_name="Doe", subscribed=True, metadata={
        "source": "website",
        "plan": "pro",
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                | Type                                                                                                     | Required                                                                                                 | Description                                                                                              | Example                                                                                                  |
| -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| `id`                                                                                                     | *str*                                                                                                    | :heavy_check_mark:                                                                                       | N/A                                                                                                      | 123e4567-e89b-12d3-a456-426614174000                                                                     |
| `email`                                                                                                  | *Optional[str]*                                                                                          | :heavy_minus_sign:                                                                                       | N/A                                                                                                      | contact@example.com                                                                                      |
| `first_name`                                                                                             | *Optional[str]*                                                                                          | :heavy_minus_sign:                                                                                       | N/A                                                                                                      | John                                                                                                     |
| `last_name`                                                                                              | *Optional[str]*                                                                                          | :heavy_minus_sign:                                                                                       | N/A                                                                                                      | Doe                                                                                                      |
| `subscribed`                                                                                             | *Optional[bool]*                                                                                         | :heavy_minus_sign:                                                                                       | N/A                                                                                                      | true                                                                                                     |
| `metadata`                                                                                               | Dict[str, [Nullable[models.UpdateContactRequestMetadata]](../../models/updatecontactrequestmetadata.md)] | :heavy_minus_sign:                                                                                       | Custom properties for the contact. Supports string, number, boolean, and date (as ISO string) values.    | {<br/>"source": "website",<br/>"plan": "pro",<br/>"active": true,<br/>"score": 100,<br/>"signup_date": "2024-01-15"<br/>} |
| `retries`                                                                                                | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                         | :heavy_minus_sign:                                                                                       | Configuration to override the default retry behavior of the client.                                      |                                                                                                          |

### Response

**[models.Contact](../../models/contact.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 401, 404                  | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## delete

Delete a contact from your organization

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteContact" method="delete" path="/v1/contacts/{id}" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.contacts.delete(id="123e4567-e89b-12d3-a456-426614174000")

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
| errors.Error              | 401, 404                  | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |