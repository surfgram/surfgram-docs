# PassportFilesFactory

Factory for creating and managing PassportFile handlers.

## Usage

The factory automatically registers all active PassportFile handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a PassportFile handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_passport_file`
- **Signature**: `@classmethod def register_passport_file(cls, passport_file_cls: Type["PassportFile"]) -> None`
- **Description**: Registers a new PassportFile handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["PassportFile"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
