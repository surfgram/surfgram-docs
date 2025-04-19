# BotCommandScopeChatAdministratorsFactory

Factory for creating and managing BotCommandScopeChatAdministrators handlers.

## Usage

The factory automatically registers all active BotCommandScopeChatAdministrators handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a BotCommandScopeChatAdministrators handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_bot_command_scope_chat_administrators`
- **Signature**: `@classmethod def register_bot_command_scope_chat_administrators(cls, bot_command_scope_chat_administrators_cls: Type["BotCommandScopeChatAdministrators"]) -> None`
- **Description**: Registers a new BotCommandScopeChatAdministrators handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["BotCommandScopeChatAdministrators"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
