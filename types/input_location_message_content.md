# InputLocationMessageContent Handler

Telegram Bot API InputLocationMessageContent type

## Usage

To create a InputLocationMessageContent handler, you need to:

1. Create a class inheriting from `InputLocationMessageContent`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import InputLocationMessageContent
from typing import Callable


class ExampleInputLocationMessageContent(InputLocationMessageContent):
    """Custom handler for InputLocationMessageContent events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_input_location_message_content"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the InputLocationMessageContent event"""
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
    """Processes the InputLocationMessageContent event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `latitude` (float): Latitude of the location in degrees
- `longitude` (float): Longitude of the location in degrees
- `horizontal_accuracy` (float): Optional. The radius of uncertainty for the location, measured in meters; 0-1500
- `live_period` (int): Optional. Period in seconds during which the location can be updated, should be between 60 and 86400, or 0x7FFFFFFF for live locations that can be edited indefinitely.
- `heading` (int): Optional. For live locations, a direction in which the user is moving, in degrees. Must be between 1 and 360 if specified.
- `proximity_alert_radius` (int): Optional. For live locations, a maximum distance for proximity alerts about approaching another chat member, in meters. Must be between 1 and 100000 if specified.
