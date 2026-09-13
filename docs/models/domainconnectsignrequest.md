# DomainConnectSignRequest


## Fields

| Field                                      | Type                                       | Required                                   | Description                                | Example                                    |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| `domain`                                   | *str*                                      | :heavy_check_mark:                         | N/A                                        | example.com                                |
| `service_id`                               | [models.ServiceID](../models/serviceid.md) | :heavy_check_mark:                         | Domain Connect template service ID         | send                                       |
| `params`                                   | Dict[str, *str*]                           | :heavy_minus_sign:                         | Optional template variable overrides       | {<br/>"region": "us-west-2"<br/>}          |