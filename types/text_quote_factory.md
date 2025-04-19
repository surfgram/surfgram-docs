# TextQuotesFactory

Factory for creating and managing TextQuote handlers.

## Usage

The factory automatically registers all active TextQuote handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a TextQuote handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_text_quote`
- **Signature**: `@classmethod def register_text_quote(cls, text_quote_cls: Type["TextQuote"]) -> None`
- **Description**: Registers a new TextQuote handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["TextQuote"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
