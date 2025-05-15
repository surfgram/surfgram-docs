# InputVenueMessageContent

Telegram Bot API InputVenueMessageContent type

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
from surfgram.types import InputVenueMessageContent

class MyInputVenueMessageContentHandler(InputVenueMessageContent):    
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
| `latitude` | `float` | Latitude of the venue in degrees |
| `longitude` | `float` | Longitude of the venue in degrees |
| `title` | `str` | Name of the venue |
| `address` | `str` | Address of the venue |
| `foursquare_id` | `str` | Optional. Foursquare identifier of the venue, if known |
| `foursquare_type` | `str` | Optional. Foursquare type of the venue, if known. (For example, "arts_entertainment/default", "arts_entertainment/aquarium" or "food/icecream".) |
| `google_place_id` | `str` | Optional. Google Places identifier of the venue |
| `google_place_type` | `str` | Optional. Google Places type of the venue. (See supported types.) |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
