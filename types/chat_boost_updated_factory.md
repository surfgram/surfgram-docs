# ChatBoostUpdatedsFactory

Factory for creating and managing ChatBoostUpdated handlers.

## Usage

The factory automatically registers all active ChatBoostUpdated handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ChatBoostUpdated handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_chat_boost_updated`
- **Signature**: `@classmethod def register_chat_boost_updated(cls, chat_boost_updated_cls: Type["ChatBoostUpdated"]) -> None`
- **Description**: Registers a new ChatBoostUpdated handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ChatBoostUpdated"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
