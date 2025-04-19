# InlineQueryResultsButtonsFactory

Factory for creating and managing InlineQueryResultsButton handlers.

## Usage

The factory automatically registers all active InlineQueryResultsButton handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InlineQueryResultsButton handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_inline_query_results_button`
- **Signature**: `@classmethod def register_inline_query_results_button(cls, inline_query_results_button_cls: Type["InlineQueryResultsButton"]) -> None`
- **Description**: Registers a new InlineQueryResultsButton handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InlineQueryResultsButton"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
