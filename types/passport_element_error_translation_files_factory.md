# PassportElementErrorTranslationFilesFactory

Factory for creating and managing PassportElementErrorTranslationFiles handlers.

## Usage

The factory automatically registers all active PassportElementErrorTranslationFiles handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a PassportElementErrorTranslationFiles handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_passport_element_error_translation_files`
- **Signature**: `@classmethod def register_passport_element_error_translation_files(cls, passport_element_error_translation_files_cls: Type["PassportElementErrorTranslationFiles"]) -> None`
- **Description**: Registers a new PassportElementErrorTranslationFiles handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["PassportElementErrorTranslationFiles"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
