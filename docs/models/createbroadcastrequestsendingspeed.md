# CreateBroadcastRequestSendingSpeed

Controls how fast emails are sent. 'auto' scales based on recipient count (recommended), 'slow' ~500/hr, 'normal' ~1000/hr, 'instant' sends as fast as possible (legacy).

## Example Usage

```python
from emailr.models import CreateBroadcastRequestSendingSpeed
value: CreateBroadcastRequestSendingSpeed = "auto"
```


## Values

- `"auto"`
- `"slow"`
- `"normal"`
- `"instant"`
