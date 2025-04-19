# PreparedInlineMessagesFactory

Factory for creating and managing PreparedInlineMessage handlers.

## Usage

The factory automatically registers all active PreparedInlineMessage handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a PreparedInlineMessage handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_prepared_inline_message`
- **Signature**: `@classmethod def register_prepared_inline_message(cls, prepared_inline_message_cls: Type["PreparedInlineMessage"]) -> None`
- **Description**: Registers a new PreparedInlineMessage handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["PreparedInlineMessage"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
