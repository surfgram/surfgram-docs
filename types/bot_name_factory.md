# BotNamesFactory

Factory for creating and managing BotName handlers.

## Usage

The factory automatically registers all active BotName handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a BotName handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_bot_name`
- **Signature**: `@classmethod def register_bot_name(cls, bot_name_cls: Type["BotName"]) -> None`
- **Description**: Registers a new BotName handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["BotName"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
