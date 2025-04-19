# VenuesFactory

Factory for creating and managing Venue handlers.

## Usage

The factory automatically registers all active Venue handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a Venue handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_venue`
- **Signature**: `@classmethod def register_venue(cls, venue_cls: Type["Venue"]) -> None`
- **Description**: Registers a new Venue handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["Venue"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
