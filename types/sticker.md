# Sticker Handler

Telegram Bot API Sticker type

## Usage

To create a Sticker handler, you need to:

1. Create a class inheriting from `Sticker`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import Sticker
from typing import Callable


class ExampleSticker(Sticker):
    """Custom handler for Sticker events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_sticker"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the Sticker event"""
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
    """Processes the Sticker event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `file_id` (str): Identifier for this file, which can be used to download or reuse the file
- `file_unique_id` (str): Unique identifier for this file, which is supposed to be the same over time and for different bots. Can't be used to download or reuse the file.
- `type` (str): Type of the sticker, currently one of "regular", "mask", "custom_emoji". The type of the sticker is independent from its format, which is determined by the fields is_animated and is_video.
- `width` (int): Sticker width
- `height` (int): Sticker height
- `is_animated` (bool): True, if the sticker is animated
- `is_video` (bool): True, if the sticker is a video sticker
- `thumbnail` (PhotoSize): Optional. Sticker thumbnail in the .WEBP or .JPG format
- `emoji` (str): Optional. Emoji associated with the sticker
- `set_name` (str): Optional. Name of the sticker set to which the sticker belongs
- `premium_animation` (File): Optional. For premium regular stickers, premium animation for the sticker
- `mask_position` (MaskPosition): Optional. For mask stickers, the position where the mask should be placed
- `custom_emoji_id` (str): Optional. For custom emoji stickers, unique identifier of the custom emoji
- `needs_repainting` (bool): Optional. True, if the sticker must be repainted to a text color in messages, the color of the Telegram Premium badge in emoji status, white color on chat photos, or another appropriate color in other places
- `file_size` (int): Optional. File size in bytes
