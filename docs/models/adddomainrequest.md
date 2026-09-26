# AddDomainRequest


## Fields

| Field                                                               | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `workspace_id`                                                      | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Existing workspace to join as an alias; omit to create a workspace. |                                                                     |
| `domain`                                                            | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 | example.com                                                         |
| `receiving_subdomain`                                               | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | mail                                                                |