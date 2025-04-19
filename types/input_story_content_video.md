# InputStoryContentVideo Handler

Telegram Bot API InputStoryContentVideo type

## Usage

To create a InputStoryContentVideo handler, you need to:

1. Create a class inheriting from `InputStoryContentVideo`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import InputStoryContentVideo
from typing import Callable


class ExampleInputStoryContentVideo(InputStoryContentVideo):
    """Custom handler for InputStoryContentVideo events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_input_story_content_video"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the InputStoryContentVideo event"""
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
    """Processes the InputStoryContentVideo event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Type of the content, must be video
- `video` (str): The video to post as a story. The video must be of the size 720x1280, streamable, encoded with H.265 codec, with key frames added each second in the MPEG4 format, and must not exceed 30 MB. The video can't be reused and can only be uploaded as a new file, so you can pass "attach://<file_attach_name>" if the video was uploaded using multipart/form-data under <file_attach_name>. More information on Sending Files »
- `duration` (float): Optional. Precise duration of the video in seconds; 0-60
- `cover_frame_timestamp` (float): Optional. Timestamp in seconds of the frame that will be used as the static cover for the story. Defaults to 0.0.
- `is_animation` (bool): Optional. Pass True if the video has no sound
