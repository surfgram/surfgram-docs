# ChatsFactory

Factory for creating and managing Chat handlers.

## Usage

The factory automatically registers all active Chat handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a Chat handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_chat`
- **Signature**: `@classmethod def register_chat(cls, chat_cls: Type["Chat"]) -> None`
- **Description**: Registers a new Chat handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["Chat"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
