# InlineQueryResultCachedVoicesFactory

Factory for creating and managing InlineQueryResultCachedVoice handlers.

## Usage

The factory automatically registers all active InlineQueryResultCachedVoice handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InlineQueryResultCachedVoice handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_inline_query_result_cached_voice`
- **Signature**: `@classmethod def register_inline_query_result_cached_voice(cls, inline_query_result_cached_voice_cls: Type["InlineQueryResultCachedVoice"]) -> None`
- **Description**: Registers a new InlineQueryResultCachedVoice handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InlineQueryResultCachedVoice"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
