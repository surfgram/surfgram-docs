# PassportElementErrorSelfiesFactory

Factory for creating and managing PassportElementErrorSelfie handlers.

## Usage

The factory automatically registers all active PassportElementErrorSelfie handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a PassportElementErrorSelfie handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_passport_element_error_selfie`
- **Signature**: `@classmethod def register_passport_element_error_selfie(cls, passport_element_error_selfie_cls: Type["PassportElementErrorSelfie"]) -> None`
- **Description**: Registers a new PassportElementErrorSelfie handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["PassportElementErrorSelfie"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
