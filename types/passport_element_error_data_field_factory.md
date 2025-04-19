# PassportElementErrorDataFieldsFactory

Factory for creating and managing PassportElementErrorDataField handlers.

## Usage

The factory automatically registers all active PassportElementErrorDataField handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a PassportElementErrorDataField handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_passport_element_error_data_field`
- **Signature**: `@classmethod def register_passport_element_error_data_field(cls, passport_element_error_data_field_cls: Type["PassportElementErrorDataField"]) -> None`
- **Description**: Registers a new PassportElementErrorDataField handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["PassportElementErrorDataField"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
