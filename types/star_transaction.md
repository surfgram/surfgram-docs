# StarTransaction Handler

Telegram Bot API StarTransaction type

## Usage

To create a StarTransaction handler, you need to:

1. Create a class inheriting from `StarTransaction`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import StarTransaction
from typing import Callable


class ExampleStarTransaction(StarTransaction):
    """Custom handler for StarTransaction events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_star_transaction"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the StarTransaction event"""
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
    """Processes the StarTransaction event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `id` (str): Unique identifier of the transaction. Coincides with the identifier of the original transaction for refund transactions. Coincides with SuccessfulPayment.telegram_payment_charge_id for successful incoming payments from users.
- `amount` (int): Integer amount of Telegram Stars transferred by the transaction
- `nanostar_amount` (int): Optional. The number of 1/1000000000 shares of Telegram Stars transferred by the transaction; from 0 to 999999999
- `date` (int): Date the transaction was created in Unix time
- `source` (TransactionPartner): Optional. Source of an incoming transaction (e.g., a user purchasing goods or services, Fragment refunding a failed withdrawal). Only for incoming transactions
- `receiver` (TransactionPartner): Optional. Receiver of an outgoing transaction (e.g., a user for a purchase refund, Fragment for a withdrawal). Only for outgoing transactions
