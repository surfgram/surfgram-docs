# GiveawayCreatedsFactory

Factory for creating and managing GiveawayCreated handlers.

## Usage

The factory automatically registers all active GiveawayCreated handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a GiveawayCreated handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_giveaway_created`
- **Signature**: `@classmethod def register_giveaway_created(cls, giveaway_created_cls: Type["GiveawayCreated"]) -> None`
- **Description**: Registers a new GiveawayCreated handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["GiveawayCreated"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
