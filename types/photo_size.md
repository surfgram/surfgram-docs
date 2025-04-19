# PhotoSize Handler

Telegram Bot API PhotoSize type

## Usage

To create a PhotoSize handler, you need to:

1. Create a class inheriting from `PhotoSize`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import PhotoSize
from typing import Callable


class ExamplePhotoSize(PhotoSize):
    """Custom handler for PhotoSize events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_photo_size"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the PhotoSize event"""
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
    """Processes the PhotoSize event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `file_id` (str): Identifier for this file, which can be used to download or reuse the file
- `file_unique_id` (str): Unique identifier for this file, which is supposed to be the same over time and for different bots. Can't be used to download or reuse the file.
- `width` (int): Photo width
- `height` (int): Photo height
- `file_size` (int): Optional. File size in bytes
