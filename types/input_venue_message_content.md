# InputVenueMessageContent Handler

Telegram Bot API InputVenueMessageContent type

## Usage

To create a InputVenueMessageContent handler, you need to:

1. Create a class inheriting from `InputVenueMessageContent`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import InputVenueMessageContent
from typing import Callable


class ExampleInputVenueMessageContent(InputVenueMessageContent):
    """Custom handler for InputVenueMessageContent events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_input_venue_message_content"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the InputVenueMessageContent event"""
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
    """Processes the InputVenueMessageContent event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `latitude` (float): Latitude of the venue in degrees
- `longitude` (float): Longitude of the venue in degrees
- `title` (str): Name of the venue
- `address` (str): Address of the venue
- `foursquare_id` (str): Optional. Foursquare identifier of the venue, if known
- `foursquare_type` (str): Optional. Foursquare type of the venue, if known. (For example, "arts_entertainment/default", "arts_entertainment/aquarium" or "food/icecream".)
- `google_place_id` (str): Optional. Google Places identifier of the venue
- `google_place_type` (str): Optional. Google Places type of the venue. (See supported types.)
