# Sequences

## Overview

### Available Operations

* [list_sequence_steps](#list_sequence_steps) - List sequence steps for a broadcast
* [create_sequence_step](#create_sequence_step) - Add a follow-up step to a broadcast sequence
* [update_sequence_step](#update_sequence_step) - Update a sequence step
* [delete_sequence_step](#delete_sequence_step) - Delete a sequence step
* [list_sequence_enrollments](#list_sequence_enrollments) - List enrollments for a broadcast sequence
* [get_sequence_stats](#get_sequence_stats) - Aggregate sequence enrollment stats for a broadcast

## list_sequence_steps

List sequence steps for a broadcast

### Example Usage

<!-- UsageSnippet language="python" operationID="listSequenceSteps" method="get" path="/v1/broadcasts/{broadcastId}/steps" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.sequences.list_sequence_steps(broadcast_id="5e81d598-64d7-4726-946f-d45a1bf895a6")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `broadcast_id`                                                      | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[List[models.SequenceStep]](../../models/.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 404                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## create_sequence_step

Add a follow-up step to a broadcast sequence

### Example Usage

<!-- UsageSnippet language="python" operationID="createSequenceStep" method="post" path="/v1/broadcasts/{broadcastId}/steps" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.sequences.create_sequence_step(broadcast_id="1dbe9218-d650-44a2-98aa-0c6a155cf6d1", delay_hours=72)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `broadcast_id`                                                      | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |                                                                     |
| `delay_hours`                                                       | *int*                                                               | :heavy_check_mark:                                                  | Hours to wait before sending this step.                             | 72                                                                  |
| `step_number`                                                       | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | Position in the sequence. If omitted, appended to the end.          |                                                                     |
| `subject`                                                           | *OptionalNullable[str]*                                             | :heavy_minus_sign:                                                  | N/A                                                                 |                                                                     |
| `html_content`                                                      | *OptionalNullable[str]*                                             | :heavy_minus_sign:                                                  | N/A                                                                 |                                                                     |
| `text_content`                                                      | *OptionalNullable[str]*                                             | :heavy_minus_sign:                                                  | N/A                                                                 |                                                                     |
| `template_id`                                                       | *OptionalNullable[str]*                                             | :heavy_minus_sign:                                                  | N/A                                                                 |                                                                     |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.SequenceStep](../../models/sequencestep.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 400, 404                  | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## update_sequence_step

Update a sequence step

### Example Usage

<!-- UsageSnippet language="python" operationID="updateSequenceStep" method="patch" path="/v1/broadcasts/{broadcastId}/steps/{stepId}" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.sequences.update_sequence_step(broadcast_id="a1674a44-d181-4aee-af7b-770805203bd6", step_id="82ec85e8-e450-401f-9909-c1d7802fa335")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `broadcast_id`                                                      | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `step_id`                                                           | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `step_number`                                                       | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `delay_hours`                                                       | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `subject`                                                           | *OptionalNullable[str]*                                             | :heavy_minus_sign:                                                  | N/A                                                                 |
| `html_content`                                                      | *OptionalNullable[str]*                                             | :heavy_minus_sign:                                                  | N/A                                                                 |
| `text_content`                                                      | *OptionalNullable[str]*                                             | :heavy_minus_sign:                                                  | N/A                                                                 |
| `template_id`                                                       | *OptionalNullable[str]*                                             | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.SequenceStep](../../models/sequencestep.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 404                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## delete_sequence_step

Delete a sequence step

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteSequenceStep" method="delete" path="/v1/broadcasts/{broadcastId}/steps/{stepId}" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.sequences.delete_sequence_step(broadcast_id="f7245328-a77c-47a5-97c9-7e5e7712d967", step_id="29bc2d58-fd17-4b41-bb66-37aa7e6fcabc")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `broadcast_id`                                                      | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `step_id`                                                           | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.Success](../../models/success.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.Error              | 404                       | application/json          |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## list_sequence_enrollments

List enrollments for a broadcast sequence

### Example Usage

<!-- UsageSnippet language="python" operationID="listSequenceEnrollments" method="get" path="/v1/broadcasts/{broadcastId}/enrollments" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.sequences.list_sequence_enrollments(broadcast_id="ed6d3b3d-37d6-4840-9356-f490fc1632c3")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                       | Type                                                                                            | Required                                                                                        | Description                                                                                     |
| ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| `broadcast_id`                                                                                  | *str*                                                                                           | :heavy_check_mark:                                                                              | N/A                                                                                             |
| `status`                                                                                        | [Optional[models.ListSequenceEnrollmentsStatus]](../../models/listsequenceenrollmentsstatus.md) | :heavy_minus_sign:                                                                              | N/A                                                                                             |
| `limit`                                                                                         | *Optional[str]*                                                                                 | :heavy_minus_sign:                                                                              | N/A                                                                                             |
| `offset`                                                                                        | *Optional[str]*                                                                                 | :heavy_minus_sign:                                                                              | N/A                                                                                             |
| `retries`                                                                                       | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                | :heavy_minus_sign:                                                                              | Configuration to override the default retry behavior of the client.                             |

### Response

**[models.ListSequenceEnrollmentsResponse](../../models/listsequenceenrollmentsresponse.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |

## get_sequence_stats

Aggregate sequence enrollment stats for a broadcast

### Example Usage

<!-- UsageSnippet language="python" operationID="getSequenceStats" method="get" path="/v1/broadcasts/{broadcastId}/sequence-stats" -->
```python
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.sequences.get_sequence_stats(broadcast_id="7f4f7973-f58d-45d4-b89f-4b6312e85b8d")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `broadcast_id`                                                      | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.SequenceStats](../../models/sequencestats.md)**

### Errors

| Error Type                | Status Code               | Content Type              |
| ------------------------- | ------------------------- | ------------------------- |
| errors.EmailrDefaultError | 4XX, 5XX                  | \*/\*                     |