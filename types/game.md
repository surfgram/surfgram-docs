# Game Handler

Telegram Bot API Game type

## Usage

To create a Game handler, you need to:

1. Create a class inheriting from `Game`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import Game
from typing import Callable


class ExampleGame(Game):
    """Custom handler for Game events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_game"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the Game event"""
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
    """Processes the Game event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `title` (str): Title of the game
- `description` (str): Description of the game
- `photo` (List[PhotoSize]): Photo that will be displayed in the game message in chats.
- `text` (str): Optional. Brief description of the game or high scores included in the game message. Can be automatically edited to include current high scores for the game when the bot calls setGameScore, or manually edited using editMessageText. 0-4096 characters.
- `text_entities` (List[MessageEntity]): Optional. Special entities that appear in text, such as usernames, URLs, bot commands, etc.
- `animation` (Animation): Optional. Animation that will be displayed in the game message in chats. Upload via BotFather
