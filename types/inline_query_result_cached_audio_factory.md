# InlineQueryResultCachedAudiosFactory

Factory for creating and managing InlineQueryResultCachedAudio handlers.

## Usage

The factory automatically registers all active InlineQueryResultCachedAudio handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InlineQueryResultCachedAudio handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_inline_query_result_cached_audio`
- **Signature**: `@classmethod def register_inline_query_result_cached_audio(cls, inline_query_result_cached_audio_cls: Type["InlineQueryResultCachedAudio"]) -> None`
- **Description**: Registers a new InlineQueryResultCachedAudio handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InlineQueryResultCachedAudio"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
