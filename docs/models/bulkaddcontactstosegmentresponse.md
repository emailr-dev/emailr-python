# BulkAddContactsToSegmentResponse


## Fields

| Field                                                     | Type                                                      | Required                                                  | Description                                               | Example                                                   |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| `added`                                                   | *int*                                                     | :heavy_check_mark:                                        | Number of contacts successfully added to the segment      | 10                                                        |
| `already_in_segment`                                      | *int*                                                     | :heavy_check_mark:                                        | Number of contacts that were already in the segment       | 2                                                         |
| `not_found`                                               | *int*                                                     | :heavy_check_mark:                                        | Number of emails that were not found in the contacts list | 1                                                         |