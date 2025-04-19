# FilesFactory

Factory for creating and managing File handlers.

## Usage

The factory automatically registers all active File handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a File handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_file`
- **Signature**: `@classmethod def register_file(cls, file_cls: Type["File"]) -> None`
- **Description**: Registers a new File handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["File"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
