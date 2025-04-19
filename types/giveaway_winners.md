# GiveawayWinners Handler

Telegram Bot API GiveawayWinners type

## Usage

To create a GiveawayWinners handler, you need to:

1. Create a class inheriting from `GiveawayWinners`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import GiveawayWinners
from typing import Callable


class ExampleGiveawayWinners(GiveawayWinners):
    """Custom handler for GiveawayWinners events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_giveaway_winners"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the GiveawayWinners event"""
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
    """Processes the GiveawayWinners event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `chat` (Chat): The chat that created the giveaway
- `giveaway_message_id` (int): Identifier of the message with the giveaway in the chat
- `winners_selection_date` (int): Point in time (Unix timestamp) when winners of the giveaway were selected
- `winner_count` (int): Total number of winners in the giveaway
- `winners` (List[User]): List of up to 100 winners of the giveaway
- `additional_chat_count` (int): Optional. The number of other chats the user had to join in order to be eligible for the giveaway
- `prize_star_count` (int): Optional. The number of Telegram Stars that were split between giveaway winners; for Telegram Star giveaways only
- `premium_subscription_month_count` (int): Optional. The number of months the Telegram Premium subscription won from the giveaway will be active for; for Telegram Premium giveaways only
- `unclaimed_prize_count` (int): Optional. Number of undistributed prizes
- `only_new_members` (bool): Optional. True, if only users who had joined the chats after the giveaway started were eligible to win
- `was_refunded` (bool): Optional. True, if the giveaway was canceled because the payment for it was refunded
- `prize_description` (str): Optional. Description of additional giveaway prize
