# MenuButtonWebApp Handler

Telegram Bot API MenuButtonWebApp type

## Usage

To create a MenuButtonWebApp handler, you need to:

1. Create a class inheriting from `MenuButtonWebApp`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import MenuButtonWebApp
from typing import Callable


class ExampleMenuButtonWebApp(MenuButtonWebApp):
    """Custom handler for MenuButtonWebApp events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_menu_button_web_app"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the MenuButtonWebApp event"""
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
    """Processes the MenuButtonWebApp event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Type of the button, must be web_app
- `text` (str): Text on the button
- `web_app` (WebAppInfo): Description of the Web App that will be launched when the user presses the button. The Web App will be able to send an arbitrary message on behalf of the user using the method answerWebAppQuery. Alternatively, a t.me link to a Web App of the bot can be specified in the object instead of the Web App's URL, in which case the Web App will be opened as if the user pressed the link.
