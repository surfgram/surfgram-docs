# InputTextMessageContentsFactory

Factory for creating and managing InputTextMessageContent handlers.

## Usage

The factory automatically registers all active InputTextMessageContent handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InputTextMessageContent handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_input_text_message_content`
- **Signature**: `@classmethod def register_input_text_message_content(cls, input_text_message_content_cls: Type["InputTextMessageContent"]) -> None`
- **Description**: Registers a new InputTextMessageContent handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InputTextMessageContent"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
