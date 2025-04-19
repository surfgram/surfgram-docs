# PassportElementErrorFiles Handler

Telegram Bot API PassportElementErrorFiles type

## Usage

To create a PassportElementErrorFiles handler, you need to:

1. Create a class inheriting from `PassportElementErrorFiles`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import PassportElementErrorFiles
from typing import Callable


class ExamplePassportElementErrorFiles(PassportElementErrorFiles):
    """Custom handler for PassportElementErrorFiles events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_passport_element_error_files"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the PassportElementErrorFiles event"""
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
    """Processes the PassportElementErrorFiles event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `source` (str): Error source, must be files
- `type` (str): The section of the user's Telegram Passport which has the issue, one of "utility_bill", "bank_statement", "rental_agreement", "passport_registration", "temporary_registration"
- `file_hashes` (List[str]): List of base64-encoded file hashes
- `message` (str): Error message
