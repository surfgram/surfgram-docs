# BusinessOpeningHoursFactory

Factory for creating and managing BusinessOpeningHours handlers.

## Usage

The factory automatically registers all active BusinessOpeningHours handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a BusinessOpeningHours handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_business_opening_hours`
- **Signature**: `@classmethod def register_business_opening_hours(cls, business_opening_hours_cls: Type["BusinessOpeningHours"]) -> None`
- **Description**: Registers a new BusinessOpeningHours handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["BusinessOpeningHours"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
