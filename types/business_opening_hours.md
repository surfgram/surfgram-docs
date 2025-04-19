# BusinessOpeningHours Handler

Telegram Bot API BusinessOpeningHours type

## Usage

To create a BusinessOpeningHours handler, you need to:

1. Create a class inheriting from `BusinessOpeningHours`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import BusinessOpeningHours
from typing import Callable


class ExampleBusinessOpeningHours(BusinessOpeningHours):
    """Custom handler for BusinessOpeningHours events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_business_opening_hours"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the BusinessOpeningHours event"""
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
    """Processes the BusinessOpeningHours event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `time_zone_name` (str): Unique name of the time zone for which the opening hours are defined
- `opening_hours` (List[BusinessOpeningHoursInterval]): List of time intervals describing business opening hours
