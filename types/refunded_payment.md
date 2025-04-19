# RefundedPayment Handler

Telegram Bot API RefundedPayment type

## Usage

To create a RefundedPayment handler, you need to:

1. Create a class inheriting from `RefundedPayment`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import RefundedPayment
from typing import Callable


class ExampleRefundedPayment(RefundedPayment):
    """Custom handler for RefundedPayment events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_refunded_payment"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the RefundedPayment event"""
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
    """Processes the RefundedPayment event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `currency` (str): Three-letter ISO 4217 currency code, or "XTR" for payments in Telegram Stars. Currently, always "XTR"
- `total_amount` (int): Total refunded price in the smallest units of the currency (integer, not float/double). For example, for a price of US$ 1.45, total_amount = 145. See the exp parameter in currencies.json, it shows the number of digits past the decimal point for each currency (2 for the majority of currencies).
- `invoice_payload` (str): Bot-specified invoice payload
- `telegram_payment_charge_id` (str): Telegram payment identifier
- `provider_payment_charge_id` (str): Optional. Provider payment identifier
