# BusinessLocationsFactory

Factory for creating and managing BusinessLocation handlers.

## Usage

The factory automatically registers all active BusinessLocation handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a BusinessLocation handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_business_location`
- **Signature**: `@classmethod def register_business_location(cls, business_location_cls: Type["BusinessLocation"]) -> None`
- **Description**: Registers a new BusinessLocation handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["BusinessLocation"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
