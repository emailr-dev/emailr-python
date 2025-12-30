# CreateSegmentRequest


## Fields

| Field                                         | Type                                          | Required                                      | Description                                   | Example                                       |
| --------------------------------------------- | --------------------------------------------- | --------------------------------------------- | --------------------------------------------- | --------------------------------------------- |
| `name`                                        | *str*                                         | :heavy_check_mark:                            | N/A                                           | Active Users                                  |
| `description`                                 | *Optional[str]*                               | :heavy_minus_sign:                            | N/A                                           | Users who opened an email in the last 30 days |
| `conditions`                                  | Dict[str, *Nullable[Any]*]                    | :heavy_check_mark:                            | N/A                                           | {<br/>"opened_email": {<br/>"within_days": 30<br/>}<br/>} |