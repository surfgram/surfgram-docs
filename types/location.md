# Location Handler

Telegram Bot API Location type

## Usage

To create a Location handler, you need to:

1. Create a class inheriting from `Location`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import Location
from typing import Callable


class ExampleLocation(Location):
    """Custom handler for Location events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_location"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the Location event"""
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
    """Processes the Location event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `latitude` (float): Latitude as defined by the sender
- `longitude` (float): Longitude as defined by the sender
- `horizontal_accuracy` (float): Optional. The radius of uncertainty for the location, measured in meters; 0-1500
- `live_period` (int): Optional. Time relative to the message sending date, during which the location can be updated; in seconds. For active live locations only.
- `heading` (int): Optional. The direction in which user is moving, in degrees; 1-360. For active live locations only.
- `proximity_alert_radius` (int): Optional. The maximum distance for proximity alerts about approaching another chat member, in meters. For sent live locations only.
