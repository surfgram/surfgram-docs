# MessageOriginHiddenUsersFactory

Factory for creating and managing MessageOriginHiddenUser handlers.

## Usage

The factory automatically registers all active MessageOriginHiddenUser handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a MessageOriginHiddenUser handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_message_origin_hidden_user`
- **Signature**: `@classmethod def register_message_origin_hidden_user(cls, message_origin_hidden_user_cls: Type["MessageOriginHiddenUser"]) -> None`
- **Description**: Registers a new MessageOriginHiddenUser handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["MessageOriginHiddenUser"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
