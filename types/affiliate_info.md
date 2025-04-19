# AffiliateInfo Handler

Telegram Bot API AffiliateInfo type

## Usage

To create a AffiliateInfo handler, you need to:

1. Create a class inheriting from `AffiliateInfo`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import AffiliateInfo
from typing import Callable


class ExampleAffiliateInfo(AffiliateInfo):
    """Custom handler for AffiliateInfo events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_affiliate_info"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the AffiliateInfo event"""
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
    """Processes the AffiliateInfo event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `affiliate_user` (User): Optional. The bot or the user that received an affiliate commission if it was received by a bot or a user
- `affiliate_chat` (Chat): Optional. The chat that received an affiliate commission if it was received by a chat
- `commission_per_mille` (int): The number of Telegram Stars received by the affiliate for each 1000 Telegram Stars received by the bot from referred users
- `amount` (int): Integer amount of Telegram Stars received by the affiliate from the transaction, rounded to 0; can be negative for refunds
- `nanostar_amount` (int): Optional. The number of 1/1000000000 shares of Telegram Stars received by the affiliate; from -999999999 to 999999999; can be negative for refunds
