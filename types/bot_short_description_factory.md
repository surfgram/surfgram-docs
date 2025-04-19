# BotShortDescriptionsFactory

Factory for creating and managing BotShortDescription handlers.

## Usage

The factory automatically registers all active BotShortDescription handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a BotShortDescription handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_bot_short_description`
- **Signature**: `@classmethod def register_bot_short_description(cls, bot_short_description_cls: Type["BotShortDescription"]) -> None`
- **Description**: Registers a new BotShortDescription handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["BotShortDescription"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
