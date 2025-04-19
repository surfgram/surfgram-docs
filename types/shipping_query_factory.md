# ShippingQueriesFactory

Factory for creating and managing ShippingQuery handlers.

## Usage

The factory automatically registers all active ShippingQuery handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ShippingQuery handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_shipping_query`
- **Signature**: `@classmethod def register_shipping_query(cls, shipping_query_cls: Type["ShippingQuery"]) -> None`
- **Description**: Registers a new ShippingQuery handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ShippingQuery"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
