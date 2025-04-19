# LocationAddressesFactory

Factory for creating and managing LocationAddress handlers.

## Usage

The factory automatically registers all active LocationAddress handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a LocationAddress handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_location_address`
- **Signature**: `@classmethod def register_location_address(cls, location_address_cls: Type["LocationAddress"]) -> None`
- **Description**: Registers a new LocationAddress handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["LocationAddress"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
