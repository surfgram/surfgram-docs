# BaseListener

Base implementation for handling Telegram bot updates with built-in polling

## Core Features
- Automatic update polling with configurable offset/timeout
- Update processing pipeline
- Integration with bot's type system
- Debug logging support

## Initialization

```python
BaseListener(offset: int = 0, timeout: int = 30)
```

**Parameters:**
- `offset`: Starting update ID (default: 0)
- `timeout`: Long polling timeout in seconds (default: 30)

## Main Methods

### `listen(bot: Bot) -> None`
Starts continuous update polling loop:
1. Fetches updates using `_get_updates`
2. Converts each to `APIObject`
3. Processes via `on_update`
4. Automatically manages update offset

### `on_update(update: APIObject, bot: Bot) -> None`
Default update handling flow:
1. Logs the raw update
2. Gets appropriate handler via `TypesFactory`
3. Creates executable instance
4. Executes the callback

### `_get_updates(bot: Bot) -> List[Dict[str, Any]]`
Internal method for fetching updates:
- Uses bot's `get_updates` API
- Returns raw update dictionaries
- Handles error cases (returns empty list on failure)

## Usage Example

```python
class CustomListener(BaseListener):
    async def on_update(self, update: APIObject, bot: Bot) -> None:
        # Custom pre-processing
        debugger.log(f"Custom handling: {update}")
        
        # Call parent implementation
        await super().on_update(update, bot)
        
        # Custom post-processing
        await bot.send_message(...)
```

## Implementation Notes
- Inherits from abstract `Listener` class
- Handles all core update processing logic
- Designed for extension (override methods as needed)
- Integrates with framework's type system automatically

> Note: This is the recommended base class for most listener implementations. Override specific methods to customize behavior while maintaining core functionality.