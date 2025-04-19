# BotCommandScopeChatsFactory

Factory for creating and managing BotCommandScopeChat handlers.

## Usage

The factory automatically registers all active BotCommandScopeChat handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a BotCommandScopeChat handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_bot_command_scope_chat`
- **Signature**: `@classmethod def register_bot_command_scope_chat(cls, bot_command_scope_chat_cls: Type["BotCommandScopeChat"]) -> None`
- **Description**: Registers a new BotCommandScopeChat handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["BotCommandScopeChat"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
