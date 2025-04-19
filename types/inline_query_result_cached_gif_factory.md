# InlineQueryResultCachedGifsFactory

Factory for creating and managing InlineQueryResultCachedGif handlers.

## Usage

The factory automatically registers all active InlineQueryResultCachedGif handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InlineQueryResultCachedGif handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_inline_query_result_cached_gif`
- **Signature**: `@classmethod def register_inline_query_result_cached_gif(cls, inline_query_result_cached_gif_cls: Type["InlineQueryResultCachedGif"]) -> None`
- **Description**: Registers a new InlineQueryResultCachedGif handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InlineQueryResultCachedGif"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
