# InlineQueryResultCachedDocumentsFactory

Factory for creating and managing InlineQueryResultCachedDocument handlers.

## Usage

The factory automatically registers all active InlineQueryResultCachedDocument handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InlineQueryResultCachedDocument handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_inline_query_result_cached_document`
- **Signature**: `@classmethod def register_inline_query_result_cached_document(cls, inline_query_result_cached_document_cls: Type["InlineQueryResultCachedDocument"]) -> None`
- **Description**: Registers a new InlineQueryResultCachedDocument handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InlineQueryResultCachedDocument"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
