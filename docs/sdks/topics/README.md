# Topics

## Overview

Broadcast topic management

### Available Operations

* [get_v1_topics](#get_v1_topics)
* [post_v1_topics](#post_v1_topics)
* [put_v1_topics_id_](#put_v1_topics_id_)
* [delete_v1_topics_id_](#delete_v1_topics_id_)

## get_v1_topics

### Example Usage

<!-- UsageSnippet language="python" operationID="get_/v1/topics" method="get" path="/v1/topics" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.topics.get_v1_topics()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.GetV1TopicsResponse](../../models/getv1topicsresponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.GetV1TopicsUnauthorizedError | 401                                 | application/json                    |
| errors.EmailrDefaultError           | 4XX, 5XX                            | \*/\*                               |

## post_v1_topics

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/v1/topics" method="post" path="/v1/topics" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.topics.post_v1_topics()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `request`                                                           | [models.PostV1TopicsRequest](../../models/postv1topicsrequest.md)   | :heavy_check_mark:                                                  | The request object to use for the request.                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.PostV1TopicsResponse](../../models/postv1topicsresponse.md)**

### Errors

| Error Type                           | Status Code                          | Content Type                         |
| ------------------------------------ | ------------------------------------ | ------------------------------------ |
| errors.PostV1TopicsUnauthorizedError | 401                                  | application/json                     |
| errors.EmailrDefaultError            | 4XX, 5XX                             | \*/\*                                |

## put_v1_topics_id_

### Example Usage

<!-- UsageSnippet language="python" operationID="put_/v1/topics/{id}" method="put" path="/v1/topics/{id}" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.topics.put_v1_topics_id_(id="ee48c911-4ed3-4c72-b979-742928fbbedc")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `name`                                                              | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `description`                                                       | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.PutV1TopicsIDResponse](../../models/putv1topicsidresponse.md)**

### Errors

| Error Type                            | Status Code                           | Content Type                          |
| ------------------------------------- | ------------------------------------- | ------------------------------------- |
| errors.PutV1TopicsIDUnauthorizedError | 401                                   | application/json                      |
| errors.PutV1TopicsIDNotFoundError     | 404                                   | application/json                      |
| errors.EmailrDefaultError             | 4XX, 5XX                              | \*/\*                                 |

## delete_v1_topics_id_

### Example Usage

<!-- UsageSnippet language="python" operationID="delete_/v1/topics/{id}" method="delete" path="/v1/topics/{id}" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.topics.delete_v1_topics_id_(id="2c9c42cd-cacd-4742-a2f5-d0ad9a9e4644")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DeleteV1TopicsIDResponse](../../models/deletev1topicsidresponse.md)**

### Errors

| Error Type                               | Status Code                              | Content Type                             |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| errors.DeleteV1TopicsIDUnauthorizedError | 401                                      | application/json                         |
| errors.DeleteV1TopicsIDNotFoundError     | 404                                      | application/json                         |
| errors.EmailrDefaultError                | 4XX, 5XX                                 | \*/\*                                    |