# InlineQueryResultLocation

Telegram Bot API InlineQueryResultLocation type

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
from surfgram.types import InlineQueryResultLocation

class MyInlineQueryResultLocationHandler(InlineQueryResultLocation):
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
| `type` | `str` | Type of the result, must be location |
| `id` | `str` | Unique identifier for this result, 1-64 Bytes |
| `latitude` | `float` | Location latitude in degrees |
| `longitude` | `float` | Location longitude in degrees |
| `title` | `str` | Location title |
| `horizontal_accuracy` | `float` | Optional. The radius of uncertainty for the location, measured in meters; 0-1500 |
| `live_period` | `int` | Optional. Period in seconds during which the location can be updated, should be between 60 and 86400, or 0x7FFFFFFF for live locations that can be edited indefinitely. |
| `heading` | `int` | Optional. For live locations, a direction in which the user is moving, in degrees. Must be between 1 and 360 if specified. |
| `proximity_alert_radius` | `int` | Optional. For live locations, a maximum distance for proximity alerts about approaching another chat member, in meters. Must be between 1 and 100000 if specified. |
| `reply_markup` | `InlineKeyboardMarkup` | Optional. Inline keyboard attached to the message |
| `input_message_content` | `InputMessageContent` | Optional. Content of the message to be sent instead of the location |
| `thumbnail_url` | `str` | Optional. Url of the thumbnail for the result |
| `thumbnail_width` | `int` | Optional. Thumbnail width |
| `thumbnail_height` | `int` | Optional. Thumbnail height |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
