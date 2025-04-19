# ChatBoostRemovedsFactory

Factory for creating and managing ChatBoostRemoved handlers.

## Usage

The factory automatically registers all active ChatBoostRemoved handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ChatBoostRemoved handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_chat_boost_removed`
- **Signature**: `@classmethod def register_chat_boost_removed(cls, chat_boost_removed_cls: Type["ChatBoostRemoved"]) -> None`
- **Description**: Registers a new ChatBoostRemoved handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ChatBoostRemoved"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
