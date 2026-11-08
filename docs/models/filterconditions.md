# FilterConditions

Filter conditions for data-driven segments. Required when type is 'data_driven'.


## Fields

| Field                                                                             | Type                                                                              | Required                                                                          | Description                                                                       | Example                                                                           |
| --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| `logic`                                                                           | [models.Logic](../models/logic.md)                                                | :heavy_check_mark:                                                                | N/A                                                                               | and                                                                               |
| `rules`                                                                           | List[[models.FilterRule](../models/filterrule.md)]                                | :heavy_check_mark:                                                                | N/A                                                                               | [<br/>{<br/>"field": "properties.plan_type",<br/>"operator": "equals",<br/>"value": "premium"<br/>}<br/>] |