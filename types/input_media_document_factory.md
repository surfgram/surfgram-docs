# InputMediaDocumentsFactory

Factory for creating and managing InputMediaDocument handlers.

## Usage

The factory automatically registers all active InputMediaDocument handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InputMediaDocument handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_input_media_document`
- **Signature**: `@classmethod def register_input_media_document(cls, input_media_document_cls: Type["InputMediaDocument"]) -> None`
- **Description**: Registers a new InputMediaDocument handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InputMediaDocument"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
