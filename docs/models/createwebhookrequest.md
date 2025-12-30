# CreateWebhookRequest


## Fields

| Field                                                | Type                                                 | Required                                             | Description                                          | Example                                              |
| ---------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------- |
| `name`                                               | *str*                                                | :heavy_check_mark:                                   | N/A                                                  | Email Events Webhook                                 |
| `url`                                                | *str*                                                | :heavy_check_mark:                                   | N/A                                                  | https://api.example.com/webhooks                     |
| `events`                                             | List[*str*]                                          | :heavy_check_mark:                                   | N/A                                                  | [<br/>"email.sent",<br/>"email.delivered",<br/>"email.bounced"<br/>] |