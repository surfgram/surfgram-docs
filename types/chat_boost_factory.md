# ChatBoostsFactory

Factory for creating and managing ChatBoost handlers.

## Usage

The factory automatically registers all active ChatBoost handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ChatBoost handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_chat_boost`
- **Signature**: `@classmethod def register_chat_boost(cls, chat_boost_cls: Type["ChatBoost"]) -> None`
- **Description**: Registers a new ChatBoost handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ChatBoost"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
