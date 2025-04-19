# Giveaway Handler

Telegram Bot API Giveaway type

## Usage

To create a Giveaway handler, you need to:

1. Create a class inheriting from `Giveaway`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import Giveaway
from typing import Callable


class ExampleGiveaway(Giveaway):
    """Custom handler for Giveaway events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_giveaway"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the Giveaway event"""
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
    """Processes the Giveaway event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `chats` (List[Chat]): The list of chats which the user must join to participate in the giveaway
- `winners_selection_date` (int): Point in time (Unix timestamp) when winners of the giveaway will be selected
- `winner_count` (int): The number of users which are supposed to be selected as winners of the giveaway
- `only_new_members` (bool): Optional. True, if only users who join the chats after the giveaway started should be eligible to win
- `has_public_winners` (bool): Optional. True, if the list of giveaway winners will be visible to everyone
- `prize_description` (str): Optional. Description of additional giveaway prize
- `country_codes` (List[str]): Optional. A list of two-letter ISO 3166-1 alpha-2 country codes indicating the countries from which eligible users for the giveaway must come. If empty, then all users can participate in the giveaway. Users with a phone number that was bought on Fragment can always participate in giveaways.
- `prize_star_count` (int): Optional. The number of Telegram Stars to be split between giveaway winners; for Telegram Star giveaways only
- `premium_subscription_month_count` (int): Optional. The number of months the Telegram Premium subscription won from the giveaway will be active for; for Telegram Premium giveaways only
