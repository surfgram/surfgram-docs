# ChatBoostSourcePremiumsFactory

Factory for creating and managing ChatBoostSourcePremium handlers.

## Usage

The factory automatically registers all active ChatBoostSourcePremium handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ChatBoostSourcePremium handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_chat_boost_source_premium`
- **Signature**: `@classmethod def register_chat_boost_source_premium(cls, chat_boost_source_premium_cls: Type["ChatBoostSourcePremium"]) -> None`
- **Description**: Registers a new ChatBoostSourcePremium handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ChatBoostSourcePremium"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
