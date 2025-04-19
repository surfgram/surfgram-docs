# BotCommandScopeDefaultsFactory

Factory for creating and managing BotCommandScopeDefault handlers.

## Usage

The factory automatically registers all active BotCommandScopeDefault handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a BotCommandScopeDefault handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_bot_command_scope_default`
- **Signature**: `@classmethod def register_bot_command_scope_default(cls, bot_command_scope_default_cls: Type["BotCommandScopeDefault"]) -> None`
- **Description**: Registers a new BotCommandScopeDefault handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["BotCommandScopeDefault"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
