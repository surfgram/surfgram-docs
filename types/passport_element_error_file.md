# PassportElementErrorFile Handler

Telegram Bot API PassportElementErrorFile type

## Usage

To create a PassportElementErrorFile handler, you need to:

1. Create a class inheriting from `PassportElementErrorFile`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import PassportElementErrorFile
from typing import Callable


class ExamplePassportElementErrorFile(PassportElementErrorFile):
    """Custom handler for PassportElementErrorFile events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_passport_element_error_file"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the PassportElementErrorFile event"""
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
    """Processes the PassportElementErrorFile event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `source` (str): Error source, must be file
- `type` (str): The section of the user's Telegram Passport which has the issue, one of "utility_bill", "bank_statement", "rental_agreement", "passport_registration", "temporary_registration"
- `file_hash` (str): Base64-encoded file hash
- `message` (str): Error message
