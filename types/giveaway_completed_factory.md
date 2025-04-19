# GiveawayCompletedsFactory

Factory for creating and managing GiveawayCompleted handlers.

## Usage

The factory automatically registers all active GiveawayCompleted handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a GiveawayCompleted handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_giveaway_completed`
- **Signature**: `@classmethod def register_giveaway_completed(cls, giveaway_completed_cls: Type["GiveawayCompleted"]) -> None`
- **Description**: Registers a new GiveawayCompleted handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["GiveawayCompleted"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
