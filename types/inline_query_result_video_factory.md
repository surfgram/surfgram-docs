# InlineQueryResultVideosFactory

Factory for creating and managing InlineQueryResultVideo handlers.

## Usage

The factory automatically registers all active InlineQueryResultVideo handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InlineQueryResultVideo handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_inline_query_result_video`
- **Signature**: `@classmethod def register_inline_query_result_video(cls, inline_query_result_video_cls: Type["InlineQueryResultVideo"]) -> None`
- **Description**: Registers a new InlineQueryResultVideo handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InlineQueryResultVideo"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
