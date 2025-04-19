# SuccessfulPayment Handler

Telegram Bot API SuccessfulPayment type

## Usage

To create a SuccessfulPayment handler, you need to:

1. Create a class inheriting from `SuccessfulPayment`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import SuccessfulPayment
from typing import Callable


class ExampleSuccessfulPayment(SuccessfulPayment):
    """Custom handler for SuccessfulPayment events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_successful_payment"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the SuccessfulPayment event"""
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
    """Processes the SuccessfulPayment event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `currency` (str): Three-letter ISO 4217 currency code, or "XTR" for payments in Telegram Stars
- `total_amount` (int): Total price in the smallest units of the currency (integer, not float/double). For example, for a price of US$ 1.45 pass amount = 145. See the exp parameter in currencies.json, it shows the number of digits past the decimal point for each currency (2 for the majority of currencies).
- `invoice_payload` (str): Bot-specified invoice payload
- `subscription_expiration_date` (int): Optional. Expiration date of the subscription, in Unix time; for recurring payments only
- `is_recurring` (bool): Optional. True, if the payment is a recurring payment for a subscription
- `is_first_recurring` (bool): Optional. True, if the payment is the first payment for a subscription
- `shipping_option_id` (str): Optional. Identifier of the shipping option chosen by the user
- `order_info` (OrderInfo): Optional. Order information provided by the user
- `telegram_payment_charge_id` (str): Telegram payment identifier
- `provider_payment_charge_id` (str): Provider payment identifier
