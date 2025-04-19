# BusinessOpeningHoursIntervalsFactory

Factory for creating and managing BusinessOpeningHoursInterval handlers.

## Usage

The factory automatically registers all active BusinessOpeningHoursInterval handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a BusinessOpeningHoursInterval handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_business_opening_hours_interval`
- **Signature**: `@classmethod def register_business_opening_hours_interval(cls, business_opening_hours_interval_cls: Type["BusinessOpeningHoursInterval"]) -> None`
- **Description**: Registers a new BusinessOpeningHoursInterval handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["BusinessOpeningHoursInterval"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
