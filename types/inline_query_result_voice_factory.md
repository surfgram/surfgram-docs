# InlineQueryResultVoicesFactory

Factory for creating and managing InlineQueryResultVoice handlers.

## Usage

The factory automatically registers all active InlineQueryResultVoice handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InlineQueryResultVoice handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_inline_query_result_voice`
- **Signature**: `@classmethod def register_inline_query_result_voice(cls, inline_query_result_voice_cls: Type["InlineQueryResultVoice"]) -> None`
- **Description**: Registers a new InlineQueryResultVoice handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InlineQueryResultVoice"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
