# ContactProperties

## Overview

### Available Operations

* [create_property_definition](#create_property_definition) - Create property definition
* [list_property_definitions](#list_property_definitions) - List property definitions
* [delete_property_definition](#delete_property_definition) - Delete property definition

## create_property_definition

Create a new contact property definition for your organization

### Example Usage

<!-- UsageSnippet language="python" operationID="createPropertyDefinition" method="post" path="/v1/contact-properties" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.contact_properties.create_property_definition(request={
        "name": "company",
        "type": "string",
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                 | Type                                                                                      | Required                                                                                  | Description                                                                               |
| ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| `request`                                                                                 | [models.CreatePropertyDefinitionRequest](../../models/createpropertydefinitionrequest.md) | :heavy_check_mark:                                                                        | The request object to use for the request.                                                |
| `retries`                                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                          | :heavy_minus_sign:                                                                        | Configuration to override the default retry behavior of the client.                       |

### Response

**[models.PropertyDefinition](../../models/propertydefinition.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 400, 401                  | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## list_property_definitions

Get all contact property definitions for your organization

### Example Usage

<!-- UsageSnippet language="python" operationID="listPropertyDefinitions" method="get" path="/v1/contact-properties" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.contact_properties.list_property_definitions()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[List[models.PropertyDefinition]](../../models/.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 401                       | application/json          |
| errors.Error              | 500                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## delete_property_definition

Delete a contact property definition. This will remove the property from all contacts.

### Example Usage

<!-- UsageSnippet language="python" operationID="deletePropertyDefinition" method="delete" path="/v1/contact-properties/{id}" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.contact_properties.delete_property_definition(id="123e4567-e89b-12d3-a456-426614174000")

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
| errors.Error              | 500                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |