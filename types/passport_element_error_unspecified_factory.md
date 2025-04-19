# PassportElementErrorUnspecifiedsFactory

Factory for creating and managing PassportElementErrorUnspecified handlers.

## Usage

The factory automatically registers all active PassportElementErrorUnspecified handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a PassportElementErrorUnspecified handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_passport_element_error_unspecified`
- **Signature**: `@classmethod def register_passport_element_error_unspecified(cls, passport_element_error_unspecified_cls: Type["PassportElementErrorUnspecified"]) -> None`
- **Description**: Registers a new PassportElementErrorUnspecified handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["PassportElementErrorUnspecified"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
