# BotCommandScopeAllChatAdministratorsFactory

Factory for creating and managing BotCommandScopeAllChatAdministrators handlers.

## Usage

The factory automatically registers all active BotCommandScopeAllChatAdministrators handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a BotCommandScopeAllChatAdministrators handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_bot_command_scope_all_chat_administrators`
- **Signature**: `@classmethod def register_bot_command_scope_all_chat_administrators(cls, bot_command_scope_all_chat_administrators_cls: Type["BotCommandScopeAllChatAdministrators"]) -> None`
- **Description**: Registers a new BotCommandScopeAllChatAdministrators handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["BotCommandScopeAllChatAdministrators"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
