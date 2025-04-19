# BotCommandScopeAllPrivateChatsFactory

Factory for creating and managing BotCommandScopeAllPrivateChats handlers.

## Usage

The factory automatically registers all active BotCommandScopeAllPrivateChats handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a BotCommandScopeAllPrivateChats handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_bot_command_scope_all_private_chats`
- **Signature**: `@classmethod def register_bot_command_scope_all_private_chats(cls, bot_command_scope_all_private_chats_cls: Type["BotCommandScopeAllPrivateChats"]) -> None`
- **Description**: Registers a new BotCommandScopeAllPrivateChats handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["BotCommandScopeAllPrivateChats"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
