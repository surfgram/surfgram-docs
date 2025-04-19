# ExternalReplyInfo Handler

Telegram Bot API ExternalReplyInfo type

## Usage

To create a ExternalReplyInfo handler, you need to:

1. Create a class inheriting from `ExternalReplyInfo`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import ExternalReplyInfo
from typing import Callable


class ExampleExternalReplyInfo(ExternalReplyInfo):
    """Custom handler for ExternalReplyInfo events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_external_reply_info"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the ExternalReplyInfo event"""
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
    """Processes the ExternalReplyInfo event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `origin` (MessageOrigin): Origin of the message replied to by the given message
- `chat` (Chat): Optional. Chat the original message belongs to. Available only if the chat is a supergroup or a channel.
- `message_id` (int): Optional. Unique message identifier inside the original chat. Available only if the original chat is a supergroup or a channel.
- `link_preview_options` (LinkPreviewOptions): Optional. Options used for link preview generation for the original message, if it is a text message
- `animation` (Animation): Optional. Message is an animation, information about the animation
- `audio` (Audio): Optional. Message is an audio file, information about the file
- `document` (Document): Optional. Message is a general file, information about the file
- `paid_media` (PaidMediaInfo): Optional. Message contains paid media; information about the paid media
- `photo` (List[PhotoSize]): Optional. Message is a photo, available sizes of the photo
- `sticker` (Sticker): Optional. Message is a sticker, information about the sticker
- `story` (Union[St, y]): Optional. Message is a forwarded story
- `video` (Video): Optional. Message is a video, information about the video
- `video_note` (VideoNote): Optional. Message is a video note, information about the video message
- `voice` (Voice): Optional. Message is a voice message, information about the file
- `has_media_spoiler` (bool): Optional. True, if the message media is covered by a spoiler animation
- `contact` (Contact): Optional. Message is a shared contact, information about the contact
- `dice` (Dice): Optional. Message is a dice with random value
- `game` (Game): Optional. Message is a game, information about the game. More about games »
- `giveaway` (Giveaway): Optional. Message is a scheduled giveaway, information about the giveaway
- `giveaway_winners` (GiveawayWinners): Optional. A giveaway with public winners was completed
- `invoice` (Invoice): Optional. Message is an invoice for a payment, information about the invoice. More about payments »
- `location` (Location): Optional. Message is a shared location, information about the location
- `poll` (Poll): Optional. Message is a native poll, information about the poll
- `venue` (Venue): Optional. Message is a venue, information about the venue
