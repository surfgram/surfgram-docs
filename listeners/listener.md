# Listener

## Package
```python
from surfgram.core.listeners import Listener
```

> **ARCHITECTURAL INTERFACE**  
> This abstract class defines the core contract for all update listeners in the Surfgram framework.  
> All concrete listener implementations must inherit from this interface.

## Class Description
The `Listener` ABC (Abstract Base Class) establishes the fundamental protocol for processing Telegram bot updates, enforcing a consistent interface across:
- Polling listeners
- Webhook listeners
- Custom listener implementations

## Interface Contract
#### Parameters
| Parameter | Type | Description |
|-----------|------|-------------|
| `update`  | `APIObject` | Normalized update container with parsed data |

#### Behavior Requirements
Implementations must:
1. Process updates within async context
2. Handle all relevant update types
3. Manage their own error handling
4. Not block indefinitely (avoid event loop starvation)

## Usage Guidelines

### Implementation Example
```python
class CustomListener(Listener):
    async def on_update(self, update: APIObject) -> None:
        if update.message:
            await process_message(update.message)
        elif update.callback_query:
            await handle_callback(update.callback_query)
```
