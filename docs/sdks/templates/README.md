# Templates

## Overview

Email template management

### Available Operations

* [get_template_preview](#get_template_preview) - Get template preview (public)
* [create](#create) - Create a template
* [list](#list) - List templates
* [get](#get) - Get template
* [update](#update) - Update template
* [delete](#delete) - Delete template
* [update_template_preview](#update_template_preview) - Update template preview
* [publish_template](#publish_template) - Publish template

## get_template_preview

Get the preview HTML for a template. This is a public route that does not require authentication, designed for AI agents to view template previews.

### Example Usage

<!-- UsageSnippet language="python" operationID="getTemplatePreview" method="get" path="/preview/{template_id}" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.templates.get_template_preview(template_id="123e4567-e89b-12d3-a456-426614174000")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `template_id`                                                       | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 | 123e4567-e89b-12d3-a456-426614174000                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[str](../../models/.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.NotFoundError      | 404                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## create

Create a new email template

### Example Usage

<!-- UsageSnippet language="python" operationID="createTemplate" method="post" path="/v1/templates" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.templates.create(request={
        "name": "Welcome Email",
        "subject": "Welcome to {{company}}",
        "html_content": "<h1>Welcome {{name}}</h1>",
        "text_content": "Welcome {{name}}",
        "variables": [
            "name",
            "company",
        ],
        "from_email": "hello@example.com",
        "reply_to": "support@example.com",
        "preview_text": "Check out what's new...",
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                             | Type                                                                  | Required                                                              | Description                                                           |
| --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| `request`                                                             | [models.CreateTemplateRequest](../../models/createtemplaterequest.md) | :heavy_check_mark:                                                    | The request object to use for the request.                            |
| `retries`                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)      | :heavy_minus_sign:                                                    | Configuration to override the default retry behavior of the client.   |

### Response

**[models.Template](../../models/template.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 500                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## list

Get all email templates for your organization

### Example Usage

<!-- UsageSnippet language="python" operationID="listTemplates" method="get" path="/v1/templates" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.templates.list()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[List[models.Template]](../../models/.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 500                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## get

Get a specific template by ID

### Example Usage

<!-- UsageSnippet language="python" operationID="getTemplate" method="get" path="/v1/templates/{id}" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.templates.get(id="123e4567-e89b-12d3-a456-426614174000")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 | 123e4567-e89b-12d3-a456-426614174000                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.Template](../../models/template.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 404                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## update

Update an existing template

### Example Usage

<!-- UsageSnippet language="python" operationID="updateTemplate" method="put" path="/v1/templates/{id}" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.templates.update(id="123e4567-e89b-12d3-a456-426614174000", name="Welcome Email", subject="Welcome to {{company}}", html_content="<h1>Welcome {{name}}</h1>", text_content="Welcome {{name}}", variables=[
        "name",
        "company",
    ], from_email="hello@example.com", reply_to="support@example.com", preview_text="Check out what's new...")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 | 123e4567-e89b-12d3-a456-426614174000                                |
| `name`                                                              | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | Welcome Email                                                       |
| `subject`                                                           | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | Welcome to {{company}}                                              |
| `html_content`                                                      | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | <h1>Welcome {{name}}</h1>                                           |
| `text_content`                                                      | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | Welcome {{name}}                                                    |
| `variables`                                                         | List[*str*]                                                         | :heavy_minus_sign:                                                  | N/A                                                                 | [<br/>"name",<br/>"company"<br/>]                                   |
| `from_email`                                                        | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Default from email address. Must match a verified domain.           | hello@example.com                                                   |
| `reply_to`                                                          | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Reply-To email address for template-based emails.                   | support@example.com                                                 |
| `preview_text`                                                      | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Preview text (preheader) shown in email clients.                    | Check out what's new...                                             |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.Template](../../models/template.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 500                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## delete

Delete a template

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteTemplate" method="delete" path="/v1/templates/{id}" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.templates.delete(id="123e4567-e89b-12d3-a456-426614174000")

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
| errors.Error              | 500                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## update_template_preview

Update the preview HTML for a template. The preview can be accessed publicly at /preview/{template_id} without authentication.

### Example Usage

<!-- UsageSnippet language="python" operationID="updateTemplatePreview" method="put" path="/v1/templates/{id}/preview" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.templates.update_template_preview(id="123e4567-e89b-12d3-a456-426614174000", html_content="<h1>Welcome {{name}}</h1><p>Preview content here</p>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 | 123e4567-e89b-12d3-a456-426614174000                                |
| `html_content`                                                      | *str*                                                               | :heavy_check_mark:                                                  | HTML content for the template preview                               | <h1>Welcome {{name}}</h1><p>Preview content here</p>                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.UpdatePreviewResponse](../../models/updatepreviewresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 400, 404                  | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## publish_template

Publish a template, which clears the preview HTML. The preview_html field will be set to NULL after this operation.

### Example Usage

<!-- UsageSnippet language="python" operationID="publishTemplate" method="post" path="/v1/templates/{id}/publish" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.templates.publish_template(id="123e4567-e89b-12d3-a456-426614174000")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 | 123e4567-e89b-12d3-a456-426614174000                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.Template](../../models/template.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 404                       | application/json          |
| errors.Error              | 500                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |