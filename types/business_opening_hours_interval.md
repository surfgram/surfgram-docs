# BusinessOpeningHoursInterval Handler

Telegram Bot API BusinessOpeningHoursInterval type

## Usage

To create a BusinessOpeningHoursInterval handler, you need to:

1. Create a class inheriting from `BusinessOpeningHoursInterval`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import BusinessOpeningHoursInterval
from typing import Callable


class ExampleBusinessOpeningHoursInterval(BusinessOpeningHoursInterval):
    """Custom handler for BusinessOpeningHoursInterval events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_business_opening_hours_interval"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the BusinessOpeningHoursInterval event"""
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
    """Processes the BusinessOpeningHoursInterval event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `opening_minute` (int): The minute's sequence number in a week, starting on Monday, marking the start of the time interval during which the business is open; 0 - 7 * 24 * 60
- `closing_minute` (int): The minute's sequence number in a week, starting on Monday, marking the end of the time interval during which the business is open; 0 - 8 * 24 * 60
