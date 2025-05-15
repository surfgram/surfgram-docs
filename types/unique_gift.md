# UniqueGift

Telegram Bot API UniqueGift type

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
from surfgram.types import UniqueGift

class MyUniqueGiftHandler(UniqueGift):    
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
| `base_name` | `str` | Human-readable name of the regular gift from which this unique gift was upgraded |
| `name` | `str` | Unique name of the gift. This name can be used in https://t.me/nft/... links and story areas |
| `number` | `int` | Unique number of the upgraded gift among gifts upgraded from the same regular gift |
| `model` | `UniqueGiftModel` | Model of the gift |
| `symbol` | `UniqueGiftSymbol` | Symbol of the gift |
| `backdrop` | `UniqueGiftBackdrop` | Backdrop of the gift |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
