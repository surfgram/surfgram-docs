# TransactionPartnerFragment Handler

Telegram Bot API TransactionPartnerFragment type

## Usage

To create a TransactionPartnerFragment handler, you need to:

1. Create a class inheriting from `TransactionPartnerFragment`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import TransactionPartnerFragment
from typing import Callable


class ExampleTransactionPartnerFragment(TransactionPartnerFragment):
    """Custom handler for TransactionPartnerFragment events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_transaction_partner_fragment"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the TransactionPartnerFragment event"""
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
    """Processes the TransactionPartnerFragment event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Type of the transaction partner, always "fragment"
- `withdrawal_state` (RevenueWithdrawalState): Optional. State of the transaction if the transaction is outgoing
