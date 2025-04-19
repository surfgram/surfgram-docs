# MessageOriginChatsFactory

Factory for creating and managing MessageOriginChat handlers.

## Usage

The factory automatically registers all active MessageOriginChat handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a MessageOriginChat handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_message_origin_chat`
- **Signature**: `@classmethod def register_message_origin_chat(cls, message_origin_chat_cls: Type["MessageOriginChat"]) -> None`
- **Description**: Registers a new MessageOriginChat handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["MessageOriginChat"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
