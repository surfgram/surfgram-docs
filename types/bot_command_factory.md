# BotCommandsFactory

Factory for creating and managing BotCommand handlers.

## Usage

The factory automatically registers all active BotCommand handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a BotCommand handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_bot_command`
- **Signature**: `@classmethod def register_bot_command(cls, bot_command_cls: Type["BotCommand"]) -> None`
- **Description**: Registers a new BotCommand handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["BotCommand"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
