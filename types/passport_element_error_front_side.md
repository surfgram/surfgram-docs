# PassportElementErrorFrontSide Handler

Telegram Bot API PassportElementErrorFrontSide type

## Usage

To create a PassportElementErrorFrontSide handler, you need to:

1. Create a class inheriting from `PassportElementErrorFrontSide`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import PassportElementErrorFrontSide
from typing import Callable


class ExamplePassportElementErrorFrontSide(PassportElementErrorFrontSide):
    """Custom handler for PassportElementErrorFrontSide events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_passport_element_error_front_side"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the PassportElementErrorFrontSide event"""
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
    """Processes the PassportElementErrorFrontSide event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `source` (str): Error source, must be front_side
- `type` (str): The section of the user's Telegram Passport which has the issue, one of "passport", "driver_license", "identity_card", "internal_passport"
- `file_hash` (str): Base64-encoded hash of the file with the front side of the document
- `message` (str): Error message
