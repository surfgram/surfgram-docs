# ChatBoostSourceGiftCodesFactory

Factory for creating and managing ChatBoostSourceGiftCode handlers.

## Usage

The factory automatically registers all active ChatBoostSourceGiftCode handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ChatBoostSourceGiftCode handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_chat_boost_source_gift_code`
- **Signature**: `@classmethod def register_chat_boost_source_gift_code(cls, chat_boost_source_gift_code_cls: Type["ChatBoostSourceGiftCode"]) -> None`
- **Description**: Registers a new ChatBoostSourceGiftCode handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ChatBoostSourceGiftCode"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
