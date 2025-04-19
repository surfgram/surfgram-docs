# InputProfilePhotoStatic Handler

Telegram Bot API InputProfilePhotoStatic type

## Usage

To create a InputProfilePhotoStatic handler, you need to:

1. Create a class inheriting from `InputProfilePhotoStatic`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import InputProfilePhotoStatic
from typing import Callable


class ExampleInputProfilePhotoStatic(InputProfilePhotoStatic):
    """Custom handler for InputProfilePhotoStatic events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_input_profile_photo_static"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the InputProfilePhotoStatic event"""
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
    """Processes the InputProfilePhotoStatic event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Type of the profile photo, must be static
- `photo` (str): The static profile photo. Profile photos can't be reused and can only be uploaded as a new file, so you can pass "attach://<file_attach_name>" if the photo was uploaded using multipart/form-data under <file_attach_name>. More information on Sending Files »
