# PassportElementErrorFrontSidesFactory

Factory for creating and managing PassportElementErrorFrontSide handlers.

## Usage

The factory automatically registers all active PassportElementErrorFrontSide handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a PassportElementErrorFrontSide handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_passport_element_error_front_side`
- **Signature**: `@classmethod def register_passport_element_error_front_side(cls, passport_element_error_front_side_cls: Type["PassportElementErrorFrontSide"]) -> None`
- **Description**: Registers a new PassportElementErrorFrontSide handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["PassportElementErrorFrontSide"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
