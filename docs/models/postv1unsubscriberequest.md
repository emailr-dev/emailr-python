# PostV1UnsubscribeRequest


## Fields

| Field              | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `email`            | *str*              | :heavy_check_mark: | N/A                |
| `organization_id`  | *str*              | :heavy_check_mark: | N/A                |
| `topic_ids`        | List[*str*]        | :heavy_minus_sign: | N/A                |
| `unsubscribe_all`  | *Optional[bool]*   | :heavy_minus_sign: | N/A                |
| `reason`           | *Optional[str]*    | :heavy_minus_sign: | N/A                |