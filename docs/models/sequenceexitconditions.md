# SequenceExitConditions

Configurable exit rules for the sequence dispatcher. Recipients matching any rule are removed from the sequence before the next follow-up.


## Fields

| Field                        | Type                         | Required                     | Description                  |
| ---------------------------- | ---------------------------- | ---------------------------- | ---------------------------- |
| `exit_if_in_segment_ids`     | List[*str*]                  | :heavy_minus_sign:           | N/A                          |
| `exit_if_not_in_segment_ids` | List[*str*]                  | :heavy_minus_sign:           | N/A                          |