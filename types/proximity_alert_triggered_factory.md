# ProximityAlertTriggeredsFactory

Factory for creating and managing ProximityAlertTriggered handlers.

## Usage

The factory automatically registers all active ProximityAlertTriggered handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ProximityAlertTriggered handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_proximity_alert_triggered`
- **Signature**: `@classmethod def register_proximity_alert_triggered(cls, proximity_alert_triggered_cls: Type["ProximityAlertTriggered"]) -> None`
- **Description**: Registers a new ProximityAlertTriggered handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ProximityAlertTriggered"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
