# UpdateContactRequest


## Fields

| Field                                  | Type                                   | Required                               | Description                            | Example                                |
| -------------------------------------- | -------------------------------------- | -------------------------------------- | -------------------------------------- | -------------------------------------- |
| `email`                                | *Optional[str]*                        | :heavy_minus_sign:                     | N/A                                    | contact@example.com                    |
| `first_name`                           | *Optional[str]*                        | :heavy_minus_sign:                     | N/A                                    | John                                   |
| `last_name`                            | *Optional[str]*                        | :heavy_minus_sign:                     | N/A                                    | Doe                                    |
| `subscribed`                           | *Optional[bool]*                       | :heavy_minus_sign:                     | N/A                                    | true                                   |
| `metadata`                             | Dict[str, *Nullable[Any]*]             | :heavy_minus_sign:                     | N/A                                    | {<br/>"source": "website",<br/>"plan": "pro"<br/>} |