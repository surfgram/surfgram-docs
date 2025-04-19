# MessagesFactory

Factory for creating and managing Message handlers.

## Usage

The factory automatically registers all active Message handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a Message handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_message`
- **Signature**: `@classmethod def register_message(cls, message_cls: Type["Message"]) -> None`
- **Description**: Registers a new Message handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["Message"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
