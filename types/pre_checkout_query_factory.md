# PreCheckoutQueriesFactory

Factory for creating and managing PreCheckoutQuery handlers.

## Usage

The factory automatically registers all active PreCheckoutQuery handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a PreCheckoutQuery handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_pre_checkout_query`
- **Signature**: `@classmethod def register_pre_checkout_query(cls, pre_checkout_query_cls: Type["PreCheckoutQuery"]) -> None`
- **Description**: Registers a new PreCheckoutQuery handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["PreCheckoutQuery"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
