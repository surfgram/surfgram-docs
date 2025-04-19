# InlineQueryResultContactsFactory

Factory for creating and managing InlineQueryResultContact handlers.

## Usage

The factory automatically registers all active InlineQueryResultContact handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InlineQueryResultContact handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_inline_query_result_contact`
- **Signature**: `@classmethod def register_inline_query_result_contact(cls, inline_query_result_contact_cls: Type["InlineQueryResultContact"]) -> None`
- **Description**: Registers a new InlineQueryResultContact handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InlineQueryResultContact"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
