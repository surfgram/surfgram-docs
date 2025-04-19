# GiveawayWinnersFactory

Factory for creating and managing GiveawayWinners handlers.

## Usage

The factory automatically registers all active GiveawayWinners handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a GiveawayWinners handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_giveaway_winners`
- **Signature**: `@classmethod def register_giveaway_winners(cls, giveaway_winners_cls: Type["GiveawayWinners"]) -> None`
- **Description**: Registers a new GiveawayWinners handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["GiveawayWinners"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
