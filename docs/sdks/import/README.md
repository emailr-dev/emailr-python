# Import

## Overview

### Available Operations

* [csv_import_preview](#csv_import_preview) - Preview CSV import
* [csv_import](#csv_import) - Import contacts from CSV

## csv_import_preview

Parse a CSV file and return column headers with a preview of the first 5 rows

### Example Usage

<!-- UsageSnippet language="python" operationID="csvImportPreview" method="post" path="/v1/contacts/import/preview" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.import_.csv_import_preview(request={
        "file_content": "ZW1haWwsZmlyc3RfbmFtZSxsYXN0X25hbWUKam9obkBleGFtcGxlLmNvbSxKb2huLERvZQ==",
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                 | Type                                                                      | Required                                                                  | Description                                                               |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `request`                                                                 | [models.CSVImportPreviewRequest](../../models/csvimportpreviewrequest.md) | :heavy_check_mark:                                                        | The request object to use for the request.                                |
| `retries`                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)          | :heavy_minus_sign:                                                        | Configuration to override the default retry behavior of the client.       |

### Response

**[models.CSVImportPreviewResponse](../../models/csvimportpreviewresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 400, 401                  | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## csv_import

Import contacts from a CSV file with column mappings. Creates new contacts or updates existing ones based on email.

### Example Usage

<!-- UsageSnippet language="python" operationID="csvImport" method="post" path="/v1/contacts/import" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.import_.csv_import(request={
        "file_content": "ZW1haWwsZmlyc3RfbmFtZSxsYXN0X25hbWUKam9obkBleGFtcGxlLmNvbSxKb2huLERvZQ==",
        "column_mappings": [
            {
                "csv_column": "Email Address",
                "property_name": "email",
            },
            {
                "csv_column": "First Name",
                "property_name": "first_name",
            },
            {
                "csv_column": "Company",
                "property_name": "company",
            },
        ],
        "segment_id": "123e4567-e89b-12d3-a456-426614174000",
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `request`                                                           | [models.CSVImportRequest](../../models/csvimportrequest.md)         | :heavy_check_mark:                                                  | The request object to use for the request.                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.CSVImportResponse](../../models/csvimportresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 400, 401                  | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |