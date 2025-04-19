# InlineQueryResultPhotosFactory

Factory for creating and managing InlineQueryResultPhoto handlers.

## Usage

The factory automatically registers all active InlineQueryResultPhoto handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InlineQueryResultPhoto handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_inline_query_result_photo`
- **Signature**: `@classmethod def register_inline_query_result_photo(cls, inline_query_result_photo_cls: Type["InlineQueryResultPhoto"]) -> None`
- **Description**: Registers a new InlineQueryResultPhoto handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InlineQueryResultPhoto"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
