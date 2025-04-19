# GameHighScore Handler

Telegram Bot API GameHighScore type

## Usage

To create a GameHighScore handler, you need to:

1. Create a class inheriting from `GameHighScore`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import GameHighScore
from typing import Callable


class ExampleGameHighScore(GameHighScore):
    """Custom handler for GameHighScore events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_game_high_score"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the GameHighScore event"""
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
    """Processes the GameHighScore event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `position` (int): Position in high score table for the game
- `user` (User): User
- `score` (int): Score
