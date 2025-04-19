# ShippingAddressesFactory

Factory for creating and managing ShippingAddress handlers.

## Usage

The factory automatically registers all active ShippingAddress handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ShippingAddress handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_shipping_address`
- **Signature**: `@classmethod def register_shipping_address(cls, shipping_address_cls: Type["ShippingAddress"]) -> None`
- **Description**: Registers a new ShippingAddress handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ShippingAddress"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
