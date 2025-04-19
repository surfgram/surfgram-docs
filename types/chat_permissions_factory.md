# ChatPermissionsFactory

Factory for creating and managing ChatPermissions handlers.

## Usage

The factory automatically registers all active ChatPermissions handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ChatPermissions handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_chat_permissions`
- **Signature**: `@classmethod def register_chat_permissions(cls, chat_permissions_cls: Type["ChatPermissions"]) -> None`
- **Description**: Registers a new ChatPermissions handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ChatPermissions"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
