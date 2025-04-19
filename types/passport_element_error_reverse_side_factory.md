# PassportElementErrorReverseSidesFactory

Factory for creating and managing PassportElementErrorReverseSide handlers.

## Usage

The factory automatically registers all active PassportElementErrorReverseSide handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a PassportElementErrorReverseSide handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_passport_element_error_reverse_side`
- **Signature**: `@classmethod def register_passport_element_error_reverse_side(cls, passport_element_error_reverse_side_cls: Type["PassportElementErrorReverseSide"]) -> None`
- **Description**: Registers a new PassportElementErrorReverseSide handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["PassportElementErrorReverseSide"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
