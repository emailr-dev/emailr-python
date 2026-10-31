# ImportErrorT


## Fields

| Field                                               | Type                                                | Required                                            | Description                                         | Example                                             |
| --------------------------------------------------- | --------------------------------------------------- | --------------------------------------------------- | --------------------------------------------------- | --------------------------------------------------- |
| `row`                                               | *int*                                               | :heavy_check_mark:                                  | Row number in the CSV (1-indexed, excluding header) | 5                                                   |
| `email`                                             | *str*                                               | :heavy_check_mark:                                  | The email value that caused the error               | invalid-email                                       |
| `error`                                             | *str*                                               | :heavy_check_mark:                                  | Description of the error                            | Invalid email format                                |