# ChatBoostSourceGiveaway Handler

Telegram Bot API ChatBoostSourceGiveaway type

## Usage

To create a ChatBoostSourceGiveaway handler, you need to:

1. Create a class inheriting from `ChatBoostSourceGiveaway`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import ChatBoostSourceGiveaway
from typing import Callable


class ExampleChatBoostSourceGiveaway(ChatBoostSourceGiveaway):
    """Custom handler for ChatBoostSourceGiveaway events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_chat_boost_source_giveaway"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the ChatBoostSourceGiveaway event"""
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
    """Processes the ChatBoostSourceGiveaway event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `source` (str): Source of the boost, always "giveaway"
- `giveaway_message_id` (int): Identifier of a message in the chat with the giveaway; the message could have been deleted already. May be 0 if the message isn't sent yet.
- `user` (User): Optional. User that won the prize in the giveaway if any; for Telegram Premium giveaways only
- `prize_star_count` (int): Optional. The number of Telegram Stars to be split between giveaway winners; for Telegram Star giveaways only
- `is_unclaimed` (bool): Optional. True, if the giveaway was completed, but there was no user to win the prize
