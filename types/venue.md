# Venue Handler

Telegram Bot API Venue type

## Usage

To create a Venue handler, you need to:

1. Create a class inheriting from `Venue`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import Venue
from typing import Callable


class ExampleVenue(Venue):
    """Custom handler for Venue events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_venue"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the Venue event"""
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
    """Processes the Venue event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `location` (Location): Venue location. Can't be a live location
- `title` (str): Name of the venue
- `address` (str): Address of the venue
- `foursquare_id` (str): Optional. Foursquare identifier of the venue
- `foursquare_type` (str): Optional. Foursquare type of the venue. (For example, "arts_entertainment/default", "arts_entertainment/aquarium" or "food/icecream".)
- `google_place_id` (str): Optional. Google Places identifier of the venue
- `google_place_type` (str): Optional. Google Places type of the venue. (See supported types.)
