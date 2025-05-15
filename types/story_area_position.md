# StoryAreaPosition

Telegram Bot API StoryAreaPosition type

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
from surfgram.types import StoryAreaPosition

class MyStoryAreaPositionHandler(StoryAreaPosition):
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
| `x_percentage` | `float` | The abscissa of the area's center, as a percentage of the media width |
| `y_percentage` | `float` | The ordinate of the area's center, as a percentage of the media height |
| `width_percentage` | `float` | The width of the area's rectangle, as a percentage of the media width |
| `height_percentage` | `float` | The height of the area's rectangle, as a percentage of the media height |
| `rotation_angle` | `float` | The clockwise rotation angle of the rectangle, in degrees; 0-360 |
| `corner_radius_percentage` | `float` | The radius of the rectangle corner rounding, as a percentage of the media width |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
