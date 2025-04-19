# InputContactMessageContentsFactory

Factory for creating and managing InputContactMessageContent handlers.

## Usage

The factory automatically registers all active InputContactMessageContent handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InputContactMessageContent handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_input_contact_message_content`
- **Signature**: `@classmethod def register_input_contact_message_content(cls, input_contact_message_content_cls: Type["InputContactMessageContent"]) -> None`
- **Description**: Registers a new InputContactMessageContent handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InputContactMessageContent"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
