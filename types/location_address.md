# LocationAddress Handler

Telegram Bot API LocationAddress type

## Usage

To create a LocationAddress handler, you need to:

1. Create a class inheriting from `LocationAddress`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import LocationAddress
from typing import Callable


class ExampleLocationAddress(LocationAddress):
    """Custom handler for LocationAddress events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_location_address"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the LocationAddress event"""
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
    """Processes the LocationAddress event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `country_code` (str): The two-letter ISO 3166-1 alpha-2 country code of the country where the location is located
- `state` (str): Optional. State of the location
- `city` (str): Optional. City of the location
- `street` (str): Optional. Street address of the location
