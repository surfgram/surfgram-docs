# InlineQueryResultCachedVideosFactory

Factory for creating and managing InlineQueryResultCachedVideo handlers.

## Usage

The factory automatically registers all active InlineQueryResultCachedVideo handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InlineQueryResultCachedVideo handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_inline_query_result_cached_video`
- **Signature**: `@classmethod def register_inline_query_result_cached_video(cls, inline_query_result_cached_video_cls: Type["InlineQueryResultCachedVideo"]) -> None`
- **Description**: Registers a new InlineQueryResultCachedVideo handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InlineQueryResultCachedVideo"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
