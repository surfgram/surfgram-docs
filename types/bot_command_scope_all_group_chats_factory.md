# BotCommandScopeAllGroupChatsFactory

Factory for creating and managing BotCommandScopeAllGroupChats handlers.

## Usage

The factory automatically registers all active BotCommandScopeAllGroupChats handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a BotCommandScopeAllGroupChats handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_bot_command_scope_all_group_chats`
- **Signature**: `@classmethod def register_bot_command_scope_all_group_chats(cls, bot_command_scope_all_group_chats_cls: Type["BotCommandScopeAllGroupChats"]) -> None`
- **Description**: Registers a new BotCommandScopeAllGroupChats handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["BotCommandScopeAllGroupChats"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
