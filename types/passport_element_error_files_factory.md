# PassportElementErrorFilesFactory

Factory for creating and managing PassportElementErrorFiles handlers.

## Usage

The factory automatically registers all active PassportElementErrorFiles handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a PassportElementErrorFiles handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_passport_element_error_files`
- **Signature**: `@classmethod def register_passport_element_error_files(cls, passport_element_error_files_cls: Type["PassportElementErrorFiles"]) -> None`
- **Description**: Registers a new PassportElementErrorFiles handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["PassportElementErrorFiles"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
