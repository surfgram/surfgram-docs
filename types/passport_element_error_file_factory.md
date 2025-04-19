# PassportElementErrorFilesFactory

Factory for creating and managing PassportElementErrorFile handlers.

## Usage

The factory automatically registers all active PassportElementErrorFile handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a PassportElementErrorFile handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_passport_element_error_file`
- **Signature**: `@classmethod def register_passport_element_error_file(cls, passport_element_error_file_cls: Type["PassportElementErrorFile"]) -> None`
- **Description**: Registers a new PassportElementErrorFile handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["PassportElementErrorFile"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
