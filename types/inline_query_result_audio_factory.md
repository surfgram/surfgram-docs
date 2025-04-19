# InlineQueryResultAudiosFactory

Factory for creating and managing InlineQueryResultAudio handlers.

## Usage

The factory automatically registers all active InlineQueryResultAudio handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InlineQueryResultAudio handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_inline_query_result_audio`
- **Signature**: `@classmethod def register_inline_query_result_audio(cls, inline_query_result_audio_cls: Type["InlineQueryResultAudio"]) -> None`
- **Description**: Registers a new InlineQueryResultAudio handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InlineQueryResultAudio"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
