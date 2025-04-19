# ChatBoostSourceGiveawaysFactory

Factory for creating and managing ChatBoostSourceGiveaway handlers.

## Usage

The factory automatically registers all active ChatBoostSourceGiveaway handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ChatBoostSourceGiveaway handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_chat_boost_source_giveaway`
- **Signature**: `@classmethod def register_chat_boost_source_giveaway(cls, chat_boost_source_giveaway_cls: Type["ChatBoostSourceGiveaway"]) -> None`
- **Description**: Registers a new ChatBoostSourceGiveaway handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ChatBoostSourceGiveaway"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
