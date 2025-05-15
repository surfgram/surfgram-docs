# Location

Telegram Bot API Location type

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
from surfgram.types import Location

class MyLocationHandler(Location):
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
| `latitude` | `float` | Latitude as defined by the sender |
| `longitude` | `float` | Longitude as defined by the sender |
| `horizontal_accuracy` | `float` | Optional. The radius of uncertainty for the location, measured in meters; 0-1500 |
| `live_period` | `int` | Optional. Time relative to the message sending date, during which the location can be updated; in seconds. For active live locations only. |
| `heading` | `int` | Optional. The direction in which user is moving, in degrees; 1-360. For active live locations only. |
| `proximity_alert_radius` | `int` | Optional. The maximum distance for proximity alerts about approaching another chat member, in meters. For sent live locations only. |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
