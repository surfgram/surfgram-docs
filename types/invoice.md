# Invoice Handler

Telegram Bot API Invoice type

## Usage

To create a Invoice handler, you need to:

1. Create a class inheriting from `Invoice`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import Invoice
from typing import Callable


class ExampleInvoice(Invoice):
    """Custom handler for Invoice events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_invoice"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the Invoice event"""
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
    """Processes the Invoice event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `title` (str): Product name
- `description` (str): Product description
- `start_parameter` (str): Unique bot deep-linking parameter that can be used to generate this invoice
- `currency` (str): Three-letter ISO 4217 currency code, or "XTR" for payments in Telegram Stars
- `total_amount` (int): Total price in the smallest units of the currency (integer, not float/double). For example, for a price of US$ 1.45 pass amount = 145. See the exp parameter in currencies.json, it shows the number of digits past the decimal point for each currency (2 for the majority of currencies).
