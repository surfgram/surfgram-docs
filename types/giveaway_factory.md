# GiveawaysFactory

Factory for creating and managing Giveaway handlers.

## Usage

The factory automatically registers all active Giveaway handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a Giveaway handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_giveaway`
- **Signature**: `@classmethod def register_giveaway(cls, giveaway_cls: Type["Giveaway"]) -> None`
- **Description**: Registers a new Giveaway handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["Giveaway"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
