# OwnedGiftRegular Handler

Telegram Bot API OwnedGiftRegular type

## Usage

To create a OwnedGiftRegular handler, you need to:

1. Create a class inheriting from `OwnedGiftRegular`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import OwnedGiftRegular
from typing import Callable


class ExampleOwnedGiftRegular(OwnedGiftRegular):
    """Custom handler for OwnedGiftRegular events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_owned_gift_regular"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the OwnedGiftRegular event"""
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
    """Processes the OwnedGiftRegular event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Type of the gift, always "regular"
- `gift` (Gift): Information about the regular gift
- `owned_gift_id` (str): Optional. Unique identifier of the gift for the bot; for gifts received on behalf of business accounts only
- `sender_user` (User): Optional. Sender of the gift if it is a known user
- `send_date` (int): Date the gift was sent in Unix time
- `text` (str): Optional. Text of the message that was added to the gift
- `entities` (List[MessageEntity]): Optional. Special entities that appear in the text
- `is_private` (bool): Optional. True, if the sender and gift text are shown only to the gift receiver; otherwise, everyone will be able to see them
- `is_saved` (bool): Optional. True, if the gift is displayed on the account's profile page; for gifts received on behalf of business accounts only
- `can_be_upgraded` (bool): Optional. True, if the gift can be upgraded to a unique gift; for gifts received on behalf of business accounts only
- `was_refunded` (bool): Optional. True, if the gift was refunded and isn't available anymore
- `convert_star_count` (int): Optional. Number of Telegram Stars that can be claimed by the receiver instead of the gift; omitted if the gift cannot be converted to Telegram Stars
- `prepaid_upgrade_star_count` (int): Optional. Number of Telegram Stars that were paid by the sender for the ability to upgrade the gift
