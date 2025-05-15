# WebhookInfo

Telegram Bot API WebhookInfo type

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
from surfgram.types import WebhookInfo

class MyWebhookInfoHandler(WebhookInfo):
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
| `url` | `str` | Webhook URL, may be empty if webhook is not set up |
| `has_custom_certificate` | `bool` | True, if a custom certificate was provided for webhook certificate checks |
| `pending_update_count` | `int` | Number of updates awaiting delivery |
| `ip_address` | `str` | Optional. Currently used webhook IP address |
| `last_error_date` | `int` | Optional. Unix time for the most recent error that happened when trying to deliver an update via webhook |
| `last_error_message` | `str` | Optional. Error message in human-readable format for the most recent error that happened when trying to deliver an update via webhook |
| `last_synchronization_error_date` | `int` | Optional. Unix time of the most recent error that happened when trying to synchronize available updates with Telegram datacenters |
| `max_connections` | `int` | Optional. The maximum allowed number of simultaneous HTTPS connections to the webhook for update delivery |
| `allowed_updates` | `List[str]` | Optional. A list of update types the bot is subscribed to. Defaults to all update types except chat_member |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
