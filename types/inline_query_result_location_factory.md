# InlineQueryResultLocationsFactory

Factory for creating and managing InlineQueryResultLocation handlers.

## Usage

The factory automatically registers all active InlineQueryResultLocation handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InlineQueryResultLocation handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_inline_query_result_location`
- **Signature**: `@classmethod def register_inline_query_result_location(cls, inline_query_result_location_cls: Type["InlineQueryResultLocation"]) -> None`
- **Description**: Registers a new InlineQueryResultLocation handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InlineQueryResultLocation"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
