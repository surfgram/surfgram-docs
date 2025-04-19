# ReplyKeyboardMarkup Handler

Telegram Bot API ReplyKeyboardMarkup type

## Usage

To create a ReplyKeyboardMarkup handler, you need to:

1. Create a class inheriting from `ReplyKeyboardMarkup`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import ReplyKeyboardMarkup
from typing import Callable


class ExampleReplyKeyboardMarkup(ReplyKeyboardMarkup):
    """Custom handler for ReplyKeyboardMarkup events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_reply_keyboard_markup"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the ReplyKeyboardMarkup event"""
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
    """Processes the ReplyKeyboardMarkup event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `keyboard` (List[KeyboardButton]): Array of button rows, each represented by an Array of KeyboardButton objects
- `is_persistent` (bool): Optional. Requests clients to always show the keyboard when the regular keyboard is hidden. Defaults to false, in which case the custom keyboard can be hidden and opened with a keyboard icon.
- `resize_keyboard` (bool): Optional. Requests clients to resize the keyboard vertically for optimal fit (e.g., make the keyboard smaller if there are just two rows of buttons). Defaults to false, in which case the custom keyboard is always of the same height as the app's standard keyboard.
- `one_time_keyboard` (bool): Optional. Requests clients to hide the keyboard as soon as it's been used. The keyboard will still be available, but clients will automatically display the usual letter-keyboard in the chat - the user can press a special button in the input field to see the custom keyboard again. Defaults to false.
- `input_field_placeholder` (str): Optional. The placeholder to be shown in the input field when the keyboard is active; 1-64 characters
- `selective` (bool): Optional. Use this parameter if you want to show the keyboard to specific users only. Targets: 1) users that are @mentioned in the text of the Message object; 2) if the bot's message is a reply to a message in the same chat and forum topic, sender of the original message.Example: A user requests to change the bot's language, bot replies to the request with a keyboard to select the new language. Other users in the group don't see the keyboard.
