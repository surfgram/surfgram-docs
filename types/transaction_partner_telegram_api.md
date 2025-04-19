# TransactionPartnerTelegramApi Handler

Telegram Bot API TransactionPartnerTelegramApi type

## Usage

To create a TransactionPartnerTelegramApi handler, you need to:

1. Create a class inheriting from `TransactionPartnerTelegramApi`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import TransactionPartnerTelegramApi
from typing import Callable


class ExampleTransactionPartnerTelegramApi(TransactionPartnerTelegramApi):
    """Custom handler for TransactionPartnerTelegramApi events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_transaction_partner_telegram_api"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the TransactionPartnerTelegramApi event"""
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
    """Processes the TransactionPartnerTelegramApi event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Type of the transaction partner, always "telegram_api"
- `request_count` (int): The number of successful requests that exceeded regular limits and were therefore billed
