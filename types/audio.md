# Audio

Telegram Bot API Audio type

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
from surfgram.types import Audio

class MyAudioHandler(Audio):    
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
| `file_id` | `str` | Identifier for this file, which can be used to download or reuse the file |
| `file_unique_id` | `str` | Unique identifier for this file, which is supposed to be the same over time and for different bots. Can't be used to download or reuse the file. |
| `duration` | `int` | Duration of the audio in seconds as defined by the sender |
| `performer` | `str` | Optional. Performer of the audio as defined by the sender or by audio tags |
| `title` | `str` | Optional. Title of the audio as defined by the sender or by audio tags |
| `file_name` | `str` | Optional. Original filename as defined by the sender |
| `mime_type` | `str` | Optional. MIME type of the file as defined by the sender |
| `file_size` | `int` | Optional. File size in bytes. It can be bigger than 2^31 and some programming languages may have difficulty/silent defects in interpreting it. But it has at most 52 significant bits, so a signed 64-bit integer or double-precision float type are safe for storing this value. |
| `thumbnail` | `PhotoSize` | Optional. Thumbnail of the album cover to which the music file belongs |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
