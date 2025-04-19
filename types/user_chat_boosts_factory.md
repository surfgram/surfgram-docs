# UserChatBoostsFactory

Factory for creating and managing UserChatBoosts handlers.

## Usage

The factory automatically registers all active UserChatBoosts handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a UserChatBoosts handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_user_chat_boosts`
- **Signature**: `@classmethod def register_user_chat_boosts(cls, user_chat_boosts_cls: Type["UserChatBoosts"]) -> None`
- **Description**: Registers a new UserChatBoosts handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["UserChatBoosts"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
