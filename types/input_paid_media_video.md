# InputPaidMediaVideo Handler

Telegram Bot API InputPaidMediaVideo type

## Usage

To create a InputPaidMediaVideo handler, you need to:

1. Create a class inheriting from `InputPaidMediaVideo`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import InputPaidMediaVideo
from typing import Callable


class ExampleInputPaidMediaVideo(InputPaidMediaVideo):
    """Custom handler for InputPaidMediaVideo events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_input_paid_media_video"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the InputPaidMediaVideo event"""
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
    """Processes the InputPaidMediaVideo event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Type of the media, must be video
- `media` (str): File to send. Pass a file_id to send a file that exists on the Telegram servers (recommended), pass an HTTP URL for Telegram to get a file from the Internet, or pass "attach://<file_attach_name>" to upload a new one using multipart/form-data under <file_attach_name> name. More information on Sending Files »
- `thumbnail` (str): Optional. Thumbnail of the file sent; can be ignored if thumbnail generation for the file is supported server-side. The thumbnail should be in JPEG format and less than 200 kB in size. A thumbnail's width and height should not exceed 320. Ignored if the file is not uploaded using multipart/form-data. Thumbnails can't be reused and can be only uploaded as a new file, so you can pass "attach://<file_attach_name>" if the thumbnail was uploaded using multipart/form-data under <file_attach_name>. More information on Sending Files »
- `cover` (str): Optional. Cover for the video in the message. Pass a file_id to send a file that exists on the Telegram servers (recommended), pass an HTTP URL for Telegram to get a file from the Internet, or pass "attach://<file_attach_name>" to upload a new one using multipart/form-data under <file_attach_name> name. More information on Sending Files »
- `start_timestamp` (int): Optional. Start timestamp for the video in the message
- `width` (int): Optional. Video width
- `height` (int): Optional. Video height
- `duration` (int): Optional. Video duration in seconds
- `supports_streaming` (bool): Optional. Pass True if the uploaded video is suitable for streaming
