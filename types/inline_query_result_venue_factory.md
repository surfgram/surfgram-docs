# InlineQueryResultVenuesFactory

Factory for creating and managing InlineQueryResultVenue handlers.

## Usage

The factory automatically registers all active InlineQueryResultVenue handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InlineQueryResultVenue handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_inline_query_result_venue`
- **Signature**: `@classmethod def register_inline_query_result_venue(cls, inline_query_result_venue_cls: Type["InlineQueryResultVenue"]) -> None`
- **Description**: Registers a new InlineQueryResultVenue handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InlineQueryResultVenue"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
