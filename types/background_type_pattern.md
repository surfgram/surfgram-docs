# BackgroundTypePattern

Telegram Bot API BackgroundTypePattern type

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
from surfgram.types import BackgroundTypePattern

class MyBackgroundTypePatternHandler(BackgroundTypePattern):    
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
| `type` | `str` | Type of the background, always "pattern" |
| `document` | `Document` | Document with the pattern |
| `fill` | `BackgroundFill` | The background fill that is combined with the pattern |
| `intensity` | `int` | Intensity of the pattern when it is shown above the filled background; 0-100 |
| `is_inverted` | `bool` | Optional. True, if the background fill must be applied only to the pattern itself. All other pixels are black in this case. For dark themes only |
| `is_moving` | `bool` | Optional. True, if the background moves slightly when the device is tilted |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
