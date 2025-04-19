# InlineQueriesFactory

Factory for creating and managing InlineQuery handlers.

## Usage

The factory automatically registers all active InlineQuery handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InlineQuery handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_inline_query`
- **Signature**: `@classmethod def register_inline_query(cls, inline_query_cls: Type["InlineQuery"]) -> None`
- **Description**: Registers a new InlineQuery handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InlineQuery"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
