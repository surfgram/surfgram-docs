# StarTransactions Handler

Telegram Bot API StarTransactions type

## Usage

To create a StarTransactions handler, you need to:

1. Create a class inheriting from `StarTransactions`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import StarTransactions
from typing import Callable


class ExampleStarTransactions(StarTransactions):
    """Custom handler for StarTransactions events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_star_transactions"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the StarTransactions event"""
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
    """Processes the StarTransactions event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `transactions` (List[StarTransaction]): The list of transactions
