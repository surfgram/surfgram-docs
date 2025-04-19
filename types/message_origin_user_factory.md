# MessageOriginUsersFactory

Factory for creating and managing MessageOriginUser handlers.

## Usage

The factory automatically registers all active MessageOriginUser handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a MessageOriginUser handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_message_origin_user`
- **Signature**: `@classmethod def register_message_origin_user(cls, message_origin_user_cls: Type["MessageOriginUser"]) -> None`
- **Description**: Registers a new MessageOriginUser handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["MessageOriginUser"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
