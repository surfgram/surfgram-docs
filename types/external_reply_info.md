# ExternalReplyInfo

Telegram Bot API ExternalReplyInfo type

## Overview

| Property        | Type               | Required | Default | Description                              |
|-----------------|--------------------|----------|---------|------------------------------------------|
| `__is_active__` | `bool`             | No       | `True`  | Global handler switch                   |
| `__names__`     | `List[str]`        | No       | `[]`    | Trigger filter (empty = all)            |
| `__callback__`  | `Callable`         | **Yes**  | -       | Async handler function                  |

## Implementation Guide

### Basic Template

```python
from typing import List, Callable
from surfgram.types import ExternalReplyInfo

class MyExternalReplyInfoHandler(ExternalReplyInfo):
    """"""
    
    @property
    def __is_active__(self) -> bool:
        return True  # Set False to disable
        
    @property
    def __names__(self) -> List[str]:
        return []  # ['specific_trigger'] for filtered handling
        
    @property
    def __callback__(self) -> Callable:
        return self.process_event
        
    async def process_event(self, update: dict, bot) -> None:
        """Main handler logic"""
        # Implement your processing here
```

### Field Reference

The update object contains these fields:

| Field          | Type              | Description                     |
|----------------|-------------------|---------------------------------|
| `origin` | `MessageOrigin` | Origin of the message replied to by the given message |
| `chat` | `Chat` | Optional. Chat the original message belongs to. Available only if the chat is a supergroup or a channel. |
| `message_id` | `int` | Optional. Unique message identifier inside the original chat. Available only if the original chat is a supergroup or a channel. |
| `link_preview_options` | `LinkPreviewOptions` | Optional. Options used for link preview generation for the original message, if it is a text message |
| `animation` | `Animation` | Optional. Message is an animation, information about the animation |
| `audio` | `Audio` | Optional. Message is an audio file, information about the file |
| `document` | `Document` | Optional. Message is a general file, information about the file |
| `paid_media` | `PaidMediaInfo` | Optional. Message contains paid media; information about the paid media |
| `photo` | `List[PhotoSize]` | Optional. Message is a photo, available sizes of the photo |
| `sticker` | `Sticker` | Optional. Message is a sticker, information about the sticker |
| `story` | `Union[St, y]` | Optional. Message is a forwarded story |
| `video` | `Video` | Optional. Message is a video, information about the video |
| `video_note` | `VideoNote` | Optional. Message is a video note, information about the video message |
| `voice` | `Voice` | Optional. Message is a voice message, information about the file |
| `has_media_spoiler` | `bool` | Optional. True, if the message media is covered by a spoiler animation |
| `contact` | `Contact` | Optional. Message is a shared contact, information about the contact |
| `dice` | `Dice` | Optional. Message is a dice with random value |
| `game` | `Game` | Optional. Message is a game, information about the game. More about games » |
| `giveaway` | `Giveaway` | Optional. Message is a scheduled giveaway, information about the giveaway |
| `giveaway_winners` | `GiveawayWinners` | Optional. A giveaway with public winners was completed |
| `invoice` | `Invoice` | Optional. Message is an invoice for a payment, information about the invoice. More about payments » |
| `location` | `Location` | Optional. Message is a shared location, information about the location |
| `poll` | `Poll` | Optional. Message is a native poll, information about the poll |
| `venue` | `Venue` | Optional. Message is a venue, information about the venue |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
