# InputContactMessageContent Handler

Telegram Bot API InputContactMessageContent type

## Usage

To create a InputContactMessageContent handler, you need to:

1. Create a class inheriting from `InputContactMessageContent`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import InputContactMessageContent
from typing import Callable


class ExampleInputContactMessageContent(InputContactMessageContent):
    """Custom handler for InputContactMessageContent events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_input_contact_message_content"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the InputContactMessageContent event"""
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
    """Processes the InputContactMessageContent event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `phone_number` (str): Contact's phone number
- `first_name` (str): Contact's first name
- `last_name` (str): Optional. Contact's last name
- `vcard` (str): Optional. Additional data about the contact in the form of a vCard, 0-2048 bytes
