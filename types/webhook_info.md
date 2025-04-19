# WebhookInfo Handler

Telegram Bot API WebhookInfo type

## Usage

To create a WebhookInfo handler, you need to:

1. Create a class inheriting from `WebhookInfo`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import WebhookInfo
from typing import Callable


class ExampleWebhookInfo(WebhookInfo):
    """Custom handler for WebhookInfo events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_webhook_info"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the WebhookInfo event"""
        # Your implementation here
        pass
```

## Required Properties

### `__names__`
- **Type**: `List[str]`
- **Description**: List of trigger names that will activate this handler
- **Example**: `return ["start", "begin"]`

### `__callback__`
- **Type**: `Callable`
- **Description**: Returns the async function that will process the event
- **Signature**: `async def callback(update, bot) -> None`

## Handler Method

Your handler method should have the following signature:

```python
async def handle(self, update, bot):
    """Processes the WebhookInfo event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `url` (str): Webhook URL, may be empty if webhook is not set up
- `has_custom_certificate` (bool): True, if a custom certificate was provided for webhook certificate checks
- `pending_update_count` (int): Number of updates awaiting delivery
- `ip_address` (str): Optional. Currently used webhook IP address
- `last_error_date` (int): Optional. Unix time for the most recent error that happened when trying to deliver an update via webhook
- `last_error_message` (str): Optional. Error message in human-readable format for the most recent error that happened when trying to deliver an update via webhook
- `last_synchronization_error_date` (int): Optional. Unix time of the most recent error that happened when trying to synchronize available updates with Telegram datacenters
- `max_connections` (int): Optional. The maximum allowed number of simultaneous HTTPS connections to the webhook for update delivery
- `allowed_updates` (List[str]): Optional. A list of update types the bot is subscribed to. Defaults to all update types except chat_member
