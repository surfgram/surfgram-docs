# InlineQueryResultArticle

Telegram Bot API InlineQueryResultArticle type

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
from surfgram.types import InlineQueryResultArticle

class MyInlineQueryResultArticleHandler(InlineQueryResultArticle):
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
| `type` | `str` | Type of the result, must be article |
| `id` | `str` | Unique identifier for this result, 1-64 Bytes |
| `title` | `str` | Title of the result |
| `input_message_content` | `InputMessageContent` | Content of the message to be sent |
| `reply_markup` | `InlineKeyboardMarkup` | Optional. Inline keyboard attached to the message |
| `url` | `str` | Optional. URL of the result |
| `description` | `str` | Optional. Short description of the result |
| `thumbnail_url` | `str` | Optional. Url of the thumbnail for the result |
| `thumbnail_width` | `int` | Optional. Thumbnail width |
| `thumbnail_height` | `int` | Optional. Thumbnail height |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
