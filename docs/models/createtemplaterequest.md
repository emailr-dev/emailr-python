# CreateTemplateRequest


## Fields

| Field                     | Type                      | Required                  | Description               | Example                   |
| ------------------------- | ------------------------- | ------------------------- | ------------------------- | ------------------------- |
| `name`                    | *str*                     | :heavy_check_mark:        | N/A                       | Welcome Email             |
| `subject`                 | *str*                     | :heavy_check_mark:        | N/A                       | Welcome to {{company}}    |
| `html_content`            | *Optional[str]*           | :heavy_minus_sign:        | N/A                       | <h1>Welcome {{name}}</h1> |
| `text_content`            | *Optional[str]*           | :heavy_minus_sign:        | N/A                       | Welcome {{name}}          |
| `variables`               | List[*str*]               | :heavy_minus_sign:        | N/A                       | [<br/>"name",<br/>"company"<br/>] |