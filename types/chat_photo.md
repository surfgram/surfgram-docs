# ChatPhoto Handler

Telegram Bot API ChatPhoto type

## Usage

To create a ChatPhoto handler, you need to:

1. Create a class inheriting from `ChatPhoto`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import ChatPhoto
from typing import Callable


class ExampleChatPhoto(ChatPhoto):
    """Custom handler for ChatPhoto events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_chat_photo"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the ChatPhoto event"""
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
    """Processes the ChatPhoto event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `small_file_id` (str): File identifier of small (160x160) chat photo. This file_id can be used only for photo download and only for as long as the photo is not changed.
- `small_file_unique_id` (str): Unique file identifier of small (160x160) chat photo, which is supposed to be the same over time and for different bots. Can't be used to download or reuse the file.
- `big_file_id` (str): File identifier of big (640x640) chat photo. This file_id can be used only for photo download and only for as long as the photo is not changed.
- `big_file_unique_id` (str): Unique file identifier of big (640x640) chat photo, which is supposed to be the same over time and for different bots. Can't be used to download or reuse the file.
