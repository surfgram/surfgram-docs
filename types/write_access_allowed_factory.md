# WriteAccessAllowedsFactory

Factory for creating and managing WriteAccessAllowed handlers.

## Usage

The factory automatically registers all active WriteAccessAllowed handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a WriteAccessAllowed handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_write_access_allowed`
- **Signature**: `@classmethod def register_write_access_allowed(cls, write_access_allowed_cls: Type["WriteAccessAllowed"]) -> None`
- **Description**: Registers a new WriteAccessAllowed handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["WriteAccessAllowed"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
