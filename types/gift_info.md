# GiftInfo Handler

Telegram Bot API GiftInfo type

## Usage

To create a GiftInfo handler, you need to:

1. Create a class inheriting from `GiftInfo`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import GiftInfo
from typing import Callable


class ExampleGiftInfo(GiftInfo):
    """Custom handler for GiftInfo events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_gift_info"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the GiftInfo event"""
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
    """Processes the GiftInfo event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `gift` (Gift): Information about the gift
- `owned_gift_id` (str): Optional. Unique identifier of the received gift for the bot; only present for gifts received on behalf of business accounts
- `convert_star_count` (int): Optional. Number of Telegram Stars that can be claimed by the receiver by converting the gift; omitted if conversion to Telegram Stars is impossible
- `prepaid_upgrade_star_count` (int): Optional. Number of Telegram Stars that were prepaid by the sender for the ability to upgrade the gift
- `can_be_upgraded` (bool): Optional. True, if the gift can be upgraded to a unique gift
- `text` (str): Optional. Text of the message that was added to the gift
- `entities` (List[MessageEntity]): Optional. Special entities that appear in the text
- `is_private` (bool): Optional. True, if the sender and gift text are shown only to the gift receiver; otherwise, everyone will be able to see them
