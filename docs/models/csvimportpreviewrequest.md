# CSVImportPreviewRequest


## Fields

| Field                                                                    | Type                                                                     | Required                                                                 | Description                                                              | Example                                                                  |
| ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ |
| `file_content`                                                           | *str*                                                                    | :heavy_check_mark:                                                       | CSV content, either base64 encoded or raw text                           | ZW1haWwsZmlyc3RfbmFtZSxsYXN0X25hbWUKam9obkBleGFtcGxlLmNvbSxKb2huLERvZQ== |
| `is_base64`                                                              | *Optional[bool]*                                                         | :heavy_minus_sign:                                                       | Whether the file_content is base64 encoded (default: true)               | true                                                                     |