# Workspaces

## Overview

### Available Operations

* [get_current_workspace](#get_current_workspace) - Identify the domain workspace bound to the current credential

## get_current_workspace

Identify the domain workspace bound to the current credential

### Example Usage

<!-- UsageSnippet language="python" operationID="getCurrentWorkspace" method="get" path="/v1/workspaces/current" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.workspaces.get_current_workspace()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.GetCurrentWorkspaceResponse](../../models/getcurrentworkspaceresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.InternalServerError | 500                        | application/json           |
| errors.EmailrDefaultError  | 4XX, 5XX                   | \*/\*                      |