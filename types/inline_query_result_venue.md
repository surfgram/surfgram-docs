# InlineQueryResultVenue Handler

Telegram Bot API InlineQueryResultVenue type

## Usage

To create a InlineQueryResultVenue handler, you need to:

1. Create a class inheriting from `InlineQueryResultVenue`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import InlineQueryResultVenue
from typing import Callable


class ExampleInlineQueryResultVenue(InlineQueryResultVenue):
    """Custom handler for InlineQueryResultVenue events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_inline_query_result_venue"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the InlineQueryResultVenue event"""
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
    """Processes the InlineQueryResultVenue event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Type of the result, must be venue
- `id` (str): Unique identifier for this result, 1-64 Bytes
- `latitude` (float): Latitude of the venue location in degrees
- `longitude` (float): Longitude of the venue location in degrees
- `title` (str): Title of the venue
- `address` (str): Address of the venue
- `foursquare_id` (str): Optional. Foursquare identifier of the venue if known
- `foursquare_type` (str): Optional. Foursquare type of the venue, if known. (For example, "arts_entertainment/default", "arts_entertainment/aquarium" or "food/icecream".)
- `google_place_id` (str): Optional. Google Places identifier of the venue
- `google_place_type` (str): Optional. Google Places type of the venue. (See supported types.)
- `reply_markup` (InlineKeyboardMarkup): Optional. Inline keyboard attached to the message
- `input_message_content` (InputMessageContent): Optional. Content of the message to be sent instead of the venue
- `thumbnail_url` (str): Optional. Url of the thumbnail for the result
- `thumbnail_width` (int): Optional. Thumbnail width
- `thumbnail_height` (int): Optional. Thumbnail height
