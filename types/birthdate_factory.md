# BirthdatesFactory

Factory for creating and managing Birthdate handlers.

## Usage

The factory automatically registers all active Birthdate handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a Birthdate handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_birthdate`
- **Signature**: `@classmethod def register_birthdate(cls, birthdate_cls: Type["Birthdate"]) -> None`
- **Description**: Registers a new Birthdate handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["Birthdate"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
