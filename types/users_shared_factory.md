# UsersSharedsFactory

Factory for creating and managing UsersShared handlers.

## Usage

The factory automatically registers all active UsersShared handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a UsersShared handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_users_shared`
- **Signature**: `@classmethod def register_users_shared(cls, users_shared_cls: Type["UsersShared"]) -> None`
- **Description**: Registers a new UsersShared handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["UsersShared"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
