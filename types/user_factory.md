# UsersFactory

Factory for creating and managing User handlers.

## Usage

The factory automatically registers all active User handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a User handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_user`
- **Signature**: `@classmethod def register_user(cls, user_cls: Type["User"]) -> None`
- **Description**: Registers a new User handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["User"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
