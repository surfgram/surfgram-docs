# InputStoryContentPhoto Handler

Telegram Bot API InputStoryContentPhoto type

## Usage

To create a InputStoryContentPhoto handler, you need to:

1. Create a class inheriting from `InputStoryContentPhoto`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import InputStoryContentPhoto
from typing import Callable


class ExampleInputStoryContentPhoto(InputStoryContentPhoto):
    """Custom handler for InputStoryContentPhoto events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_input_story_content_photo"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the InputStoryContentPhoto event"""
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
    """Processes the InputStoryContentPhoto event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Type of the content, must be photo
- `photo` (str): The photo to post as a story. The photo must be of the size 1080x1920 and must not exceed 10 MB. The photo can't be reused and can only be uploaded as a new file, so you can pass "attach://<file_attach_name>" if the photo was uploaded using multipart/form-data under <file_attach_name>. More information on Sending Files »
