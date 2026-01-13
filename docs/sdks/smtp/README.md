# Smtp

## Overview

SMTP credentials for email sending

### Available Operations

* [get_smtp_credentials](#get_smtp_credentials) - Get SMTP credentials

## get_smtp_credentials

Get SMTP server credentials for sending emails. The password is your API key.

### Example Usage

<!-- UsageSnippet language="python" operationID="getSmtpCredentials" method="get" path="/v1/smtp/credentials" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.smtp.get_smtp_credentials()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.SMTPCredentials](../../models/smtpcredentials.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 401                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |