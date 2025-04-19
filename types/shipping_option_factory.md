# ShippingOptionsFactory

Factory for creating and managing ShippingOption handlers.

## Usage

The factory automatically registers all active ShippingOption handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ShippingOption handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_shipping_option`
- **Signature**: `@classmethod def register_shipping_option(cls, shipping_option_cls: Type["ShippingOption"]) -> None`
- **Description**: Registers a new ShippingOption handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ShippingOption"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
