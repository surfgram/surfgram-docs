# LinkPreviewOptions Handler

Telegram Bot API LinkPreviewOptions type

## Usage

To create a LinkPreviewOptions handler, you need to:

1. Create a class inheriting from `LinkPreviewOptions`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import LinkPreviewOptions
from typing import Callable


class ExampleLinkPreviewOptions(LinkPreviewOptions):
    """Custom handler for LinkPreviewOptions events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_link_preview_options"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the LinkPreviewOptions event"""
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
    """Processes the LinkPreviewOptions event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `is_disabled` (bool): Optional. True, if the link preview is disabled
- `url` (str): Optional. URL to use for the link preview. If empty, then the first URL found in the message text will be used
- `prefer_small_media` (bool): Optional. True, if the media in the link preview is supposed to be shrunk; ignored if the URL isn't explicitly specified or media size change isn't supported for the preview
- `prefer_large_media` (bool): Optional. True, if the media in the link preview is supposed to be enlarged; ignored if the URL isn't explicitly specified or media size change isn't supported for the preview
- `show_above_text` (bool): Optional. True, if the link preview must be shown above the message text; otherwise, the link preview will be shown below the message text
