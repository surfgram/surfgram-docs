# BotCommandScopeChatMembersFactory

Factory for creating and managing BotCommandScopeChatMember handlers.

## Usage

The factory automatically registers all active BotCommandScopeChatMember handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a BotCommandScopeChatMember handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_bot_command_scope_chat_member`
- **Signature**: `@classmethod def register_bot_command_scope_chat_member(cls, bot_command_scope_chat_member_cls: Type["BotCommandScopeChatMember"]) -> None`
- **Description**: Registers a new BotCommandScopeChatMember handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["BotCommandScopeChatMember"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
