# InlineQueryResultGif

Telegram Bot API InlineQueryResultGif type

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
from surfgram.types import InlineQueryResultGif

class MyInlineQueryResultGifHandler(InlineQueryResultGif):
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
| `type` | `str` | Type of the result, must be gif |
| `id` | `str` | Unique identifier for this result, 1-64 bytes |
| `gif_url` | `str` | A valid URL for the GIF file |
| `gif_width` | `int` | Optional. Width of the GIF |
| `gif_height` | `int` | Optional. Height of the GIF |
| `gif_duration` | `int` | Optional. Duration of the GIF in seconds |
| `thumbnail_url` | `str` | URL of the static (JPEG or GIF) or animated (MPEG4) thumbnail for the result |
| `thumbnail_mime_type` | `str` | Optional. MIME type of the thumbnail, must be one of "image/jpeg", "image/gif", or "video/mp4". Defaults to "image/jpeg" |
| `title` | `str` | Optional. Title for the result |
| `caption` | `str` | Optional. Caption of the GIF file to be sent, 0-1024 characters after entities parsing |
| `parse_mode` | `str` | Optional. Mode for parsing entities in the caption. See formatting options for more details. |
| `caption_entities` | `List[MessageEntity]` | Optional. List of special entities that appear in the caption, which can be specified instead of parse_mode |
| `show_caption_above_media` | `bool` | Optional. Pass True, if the caption must be shown above the message media |
| `reply_markup` | `InlineKeyboardMarkup` | Optional. Inline keyboard attached to the message |
| `input_message_content` | `InputMessageContent` | Optional. Content of the message to be sent instead of the GIF animation |
| `type` | `str` | Type of the result, must be mpeg4_gif |
| `id` | `str` | Unique identifier for this result, 1-64 bytes |
| `mpeg4_url` | `str` | A valid URL for the MPEG4 file |
| `mpeg4_width` | `int` | Optional. Video width |
| `mpeg4_height` | `int` | Optional. Video height |
| `mpeg4_duration` | `int` | Optional. Video duration in seconds |
| `thumbnail_url` | `str` | URL of the static (JPEG or GIF) or animated (MPEG4) thumbnail for the result |
| `thumbnail_mime_type` | `str` | Optional. MIME type of the thumbnail, must be one of "image/jpeg", "image/gif", or "video/mp4". Defaults to "image/jpeg" |
| `title` | `str` | Optional. Title for the result |
| `caption` | `str` | Optional. Caption of the MPEG-4 file to be sent, 0-1024 characters after entities parsing |
| `parse_mode` | `str` | Optional. Mode for parsing entities in the caption. See formatting options for more details. |
| `caption_entities` | `List[MessageEntity]` | Optional. List of special entities that appear in the caption, which can be specified instead of parse_mode |
| `show_caption_above_media` | `bool` | Optional. Pass True, if the caption must be shown above the message media |
| `reply_markup` | `InlineKeyboardMarkup` | Optional. Inline keyboard attached to the message |
| `input_message_content` | `InputMessageContent` | Optional. Content of the message to be sent instead of the video animation |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
