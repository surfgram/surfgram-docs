# PassportDataFactory

Factory for creating and managing PassportData handlers.

## Usage

The factory automatically registers all active PassportData handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a PassportData handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_passport_data`
- **Signature**: `@classmethod def register_passport_data(cls, passport_data_cls: Type["PassportData"]) -> None`
- **Description**: Registers a new PassportData handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["PassportData"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
