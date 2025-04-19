# BackgroundTypeWallpaper Handler

Telegram Bot API BackgroundTypeWallpaper type

## Usage

To create a BackgroundTypeWallpaper handler, you need to:

1. Create a class inheriting from `BackgroundTypeWallpaper`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import BackgroundTypeWallpaper
from typing import Callable


class ExampleBackgroundTypeWallpaper(BackgroundTypeWallpaper):
    """Custom handler for BackgroundTypeWallpaper events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_background_type_wallpaper"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the BackgroundTypeWallpaper event"""
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
    """Processes the BackgroundTypeWallpaper event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Type of the background, always "wallpaper"
- `document` (Document): Document with the wallpaper
- `dark_theme_dimming` (int): Dimming of the background in dark themes, as a percentage; 0-100
- `is_blurred` (bool): Optional. True, if the wallpaper is downscaled to fit in a 450x450 square and then box-blurred with radius 12
- `is_moving` (bool): Optional. True, if the background moves slightly when the device is tilted
