# ChatBoost Handler

Telegram Bot API ChatBoost type

## Usage

To create a ChatBoost handler, you need to:

1. Create a class inheriting from `ChatBoost`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import ChatBoost
from typing import Callable


class ExampleChatBoost(ChatBoost):
    """Custom handler for ChatBoost events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_chat_boost"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the ChatBoost event"""
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
    """Processes the ChatBoost event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `boost_id` (str): Unique identifier of the boost
- `add_date` (int): Point in time (Unix timestamp) when the chat was boosted
- `expiration_date` (int): Point in time (Unix timestamp) when the boost will automatically expire, unless the booster's Telegram Premium subscription is prolonged
- `source` (ChatBoostSource): Source of the added boost
