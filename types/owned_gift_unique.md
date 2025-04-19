# OwnedGiftUnique Handler

Telegram Bot API OwnedGiftUnique type

## Usage

To create a OwnedGiftUnique handler, you need to:

1. Create a class inheriting from `OwnedGiftUnique`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import OwnedGiftUnique
from typing import Callable


class ExampleOwnedGiftUnique(OwnedGiftUnique):
    """Custom handler for OwnedGiftUnique events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_owned_gift_unique"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the OwnedGiftUnique event"""
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
    """Processes the OwnedGiftUnique event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Type of the gift, always "unique"
- `gift` (UniqueGift): Information about the unique gift
- `owned_gift_id` (str): Optional. Unique identifier of the received gift for the bot; for gifts received on behalf of business accounts only
- `sender_user` (User): Optional. Sender of the gift if it is a known user
- `send_date` (int): Date the gift was sent in Unix time
- `is_saved` (bool): Optional. True, if the gift is displayed on the account's profile page; for gifts received on behalf of business accounts only
- `can_be_transferred` (bool): Optional. True, if the gift can be transferred to another owner; for gifts received on behalf of business accounts only
- `transfer_star_count` (int): Optional. Number of Telegram Stars that must be paid to transfer the gift; omitted if the bot cannot transfer the gift
