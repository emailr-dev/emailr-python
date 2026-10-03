<!-- Start SDK Example Usage [usage] -->
```python
# Synchronous Example
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.templates.get_template_preview(template_id="123e4567-e89b-12d3-a456-426614174000")

    # Handle response
    print(res)
```

</br>

The same SDK client can also be used to make asynchronous requests by importing asyncio.

```python
# Asynchronous Example
import asyncio
from emailr import Emailr
import os

async def main():

    async with Emailr(
        bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
    ) as e_client:

        res = await e_client.templates.get_template_preview_async(template_id="123e4567-e89b-12d3-a456-426614174000")

        # Handle response
        print(res)

asyncio.run(main())
```
<!-- End SDK Example Usage [usage] -->