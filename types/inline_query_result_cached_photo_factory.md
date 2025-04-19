# InlineQueryResultCachedPhotosFactory

Factory for creating and managing InlineQueryResultCachedPhoto handlers.

## Usage

The factory automatically registers all active InlineQueryResultCachedPhoto handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InlineQueryResultCachedPhoto handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_inline_query_result_cached_photo`
- **Signature**: `@classmethod def register_inline_query_result_cached_photo(cls, inline_query_result_cached_photo_cls: Type["InlineQueryResultCachedPhoto"]) -> None`
- **Description**: Registers a new InlineQueryResultCachedPhoto handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InlineQueryResultCachedPhoto"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
