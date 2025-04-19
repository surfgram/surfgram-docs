# Contact Handler

Telegram Bot API Contact type

## Usage

To create a Contact handler, you need to:

1. Create a class inheriting from `Contact`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import Contact
from typing import Callable


class ExampleContact(Contact):
    """Custom handler for Contact events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_contact"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the Contact event"""
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
    """Processes the Contact event
    
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
- `user_id` (int): Optional. Contact's user identifier in Telegram. This number may have more than 32 significant bits and some programming languages may have difficulty/silent defects in interpreting it. But it has at most 52 significant bits, so a 64-bit integer or double-precision float type are safe for storing this identifier.
- `vcard` (str): Optional. Additional data about the contact in the form of a vCard
