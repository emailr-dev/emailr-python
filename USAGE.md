<!-- Start SDK Example Usage [usage] -->
```python
# Synchronous Example
from emailr import Emailr
import os


with Emailr(
    bearer_auth=os.getenv("EMAILR_BEARER_AUTH", ""),
) as e_client:

    res = e_client.emails.send(request={
        "from_": "sender@example.com",
        "to": "recipient@example.com",
        "subject": "Hello World",
        "html": "<h1>Hello</h1>",
        "text": "Hello",
        "template_id": "123e4567-e89b-12d3-a456-426614174000",
        "template_data": {
            "name": "John",
            "company": "Acme",
        },
        "tags": {
            "campaign": "welcome",
            "source": "signup",
        },
        "attachments": [
            {
                "filename": "document.pdf",
                "content": "JVBERi0xLjQKJe...",
                "content_type": "application/pdf",
            },
        ],
        "reply_to": {
            "in_reply_to": "<message-id@domain.com>",
            "thread_id": "123e4567-e89b-12d3-a456-426614174000",
            "parent_email_id": "123e4567-e89b-12d3-a456-426614174000",
        },
    })

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

        res = await e_client.emails.send_async(request={
            "from_": "sender@example.com",
            "to": "recipient@example.com",
            "subject": "Hello World",
            "html": "<h1>Hello</h1>",
            "text": "Hello",
            "template_id": "123e4567-e89b-12d3-a456-426614174000",
            "template_data": {
                "name": "John",
                "company": "Acme",
            },
            "tags": {
                "campaign": "welcome",
                "source": "signup",
            },
            "attachments": [
                {
                    "filename": "document.pdf",
                    "content": "JVBERi0xLjQKJe...",
                    "content_type": "application/pdf",
                },
            ],
            "reply_to": {
                "in_reply_to": "<message-id@domain.com>",
                "thread_id": "123e4567-e89b-12d3-a456-426614174000",
                "parent_email_id": "123e4567-e89b-12d3-a456-426614174000",
            },
        })

        # Handle response
        print(res)

asyncio.run(main())
```
<!-- End SDK Example Usage [usage] -->