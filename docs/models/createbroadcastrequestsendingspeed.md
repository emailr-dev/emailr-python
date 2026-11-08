# CreateBroadcastRequestSendingSpeed

Controls how fast emails are sent. 'auto' scales with recipient count (recommended), 'warmup' ~100/day, 'very_slow' ~100/hr, 'slow' ~1000/hr, 'normal' ~2000/hr, 'instant' sends as fast as possible.

## Example Usage

```python
from emailr.models import CreateBroadcastRequestSendingSpeed
value: CreateBroadcastRequestSendingSpeed = "auto"
```


## Values

- `"auto"`
- `"warmup"`
- `"very_slow"`
- `"slow"`
- `"normal"`
- `"instant"`
