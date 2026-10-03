# UpdateDomainRequestReceivingSubdomain

Choose mail for subdomain receiving or @ for root; existing mail domains retain mail as a legacy receiving alias after switching to root.

## Example Usage

```python
from emailr.models import UpdateDomainRequestReceivingSubdomain
value: UpdateDomainRequestReceivingSubdomain = "mail"
```


## Values

- `"mail"`
- `"@"`
