# InlineQueryResultCachedVideo

Telegram Bot API InlineQueryResultCachedVideo type

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
from surfgram.types import InlineQueryResultCachedVideo

class MyInlineQueryResultCachedVideoHandler(InlineQueryResultCachedVideo):
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
| `type` | `str` | Type of the result, must be video |
| `id` | `str` | Unique identifier for this result, 1-64 bytes |
| `video_file_id` | `str` | A valid file identifier for the video file |
| `title` | `str` | Title for the result |
| `description` | `str` | Optional. Short description of the result |
| `caption` | `str` | Optional. Caption of the video to be sent, 0-1024 characters after entities parsing |
| `parse_mode` | `str` | Optional. Mode for parsing entities in the video caption. See formatting options for more details. |
| `caption_entities` | `List[MessageEntity]` | Optional. List of special entities that appear in the caption, which can be specified instead of parse_mode |
| `show_caption_above_media` | `bool` | Optional. Pass True, if the caption must be shown above the message media |
| `reply_markup` | `InlineKeyboardMarkup` | Optional. Inline keyboard attached to the message |
| `input_message_content` | `InputMessageContent` | Optional. Content of the message to be sent instead of the video |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
