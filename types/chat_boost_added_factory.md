# ChatBoostAddedsFactory

Factory for creating and managing ChatBoostAdded handlers.

## Usage

The factory automatically registers all active ChatBoostAdded handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ChatBoostAdded handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_chat_boost_added`
- **Signature**: `@classmethod def register_chat_boost_added(cls, chat_boost_added_cls: Type["ChatBoostAdded"]) -> None`
- **Description**: Registers a new ChatBoostAdded handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ChatBoostAdded"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
