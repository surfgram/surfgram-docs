# ShippingAddress Handler

Telegram Bot API ShippingAddress type

## Usage

To create a ShippingAddress handler, you need to:

1. Create a class inheriting from `ShippingAddress`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import ShippingAddress
from typing import Callable


class ExampleShippingAddress(ShippingAddress):
    """Custom handler for ShippingAddress events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_shipping_address"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the ShippingAddress event"""
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
    """Processes the ShippingAddress event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `country_code` (str): Two-letter ISO 3166-1 alpha-2 country code
- `state` (str): State, if applicable
- `city` (str): City
- `street_line1` (str): First line for the address
- `street_line2` (str): Second line for the address
- `post_code` (str): Address post code
