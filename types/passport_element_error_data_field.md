# PassportElementErrorDataField Handler

Telegram Bot API PassportElementErrorDataField type

## Usage

To create a PassportElementErrorDataField handler, you need to:

1. Create a class inheriting from `PassportElementErrorDataField`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import PassportElementErrorDataField
from typing import Callable


class ExamplePassportElementErrorDataField(PassportElementErrorDataField):
    """Custom handler for PassportElementErrorDataField events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_passport_element_error_data_field"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the PassportElementErrorDataField event"""
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
    """Processes the PassportElementErrorDataField event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `source` (str): Error source, must be data
- `type` (str): The section of the user's Telegram Passport which has the error, one of "personal_details", "passport", "driver_license", "identity_card", "internal_passport", "address"
- `field_name` (str): Name of the data field which has the error
- `data_hash` (str): Base64-encoded data hash
- `message` (str): Error message
