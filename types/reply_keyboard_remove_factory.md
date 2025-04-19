# ReplyKeyboardRemovesFactory

Factory for creating and managing ReplyKeyboardRemove handlers.

## Usage

The factory automatically registers all active ReplyKeyboardRemove handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ReplyKeyboardRemove handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_reply_keyboard_remove`
- **Signature**: `@classmethod def register_reply_keyboard_remove(cls, reply_keyboard_remove_cls: Type["ReplyKeyboardRemove"]) -> None`
- **Description**: Registers a new ReplyKeyboardRemove handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ReplyKeyboardRemove"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
