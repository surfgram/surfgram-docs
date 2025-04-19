# TransactionPartnerAffiliateProgram Handler

Telegram Bot API TransactionPartnerAffiliateProgram type

## Usage

To create a TransactionPartnerAffiliateProgram handler, you need to:

1. Create a class inheriting from `TransactionPartnerAffiliateProgram`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import TransactionPartnerAffiliateProgram
from typing import Callable


class ExampleTransactionPartnerAffiliateProgram(TransactionPartnerAffiliateProgram):
    """Custom handler for TransactionPartnerAffiliateProgram events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_transaction_partner_affiliate_program"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the TransactionPartnerAffiliateProgram event"""
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
    """Processes the TransactionPartnerAffiliateProgram event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Type of the transaction partner, always "affiliate_program"
- `sponsor_user` (User): Optional. Information about the bot that sponsored the affiliate program
- `commission_per_mille` (int): The number of Telegram Stars received by the bot for each 1000 Telegram Stars received by the affiliate program sponsor from referred users
