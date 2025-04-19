# ReplyKeyboardMarkupsFactory

Factory for creating and managing ReplyKeyboardMarkup handlers.

## Usage

The factory automatically registers all active ReplyKeyboardMarkup handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ReplyKeyboardMarkup handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_reply_keyboard_markup`
- **Signature**: `@classmethod def register_reply_keyboard_markup(cls, reply_keyboard_markup_cls: Type["ReplyKeyboardMarkup"]) -> None`
- **Description**: Registers a new ReplyKeyboardMarkup handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ReplyKeyboardMarkup"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
