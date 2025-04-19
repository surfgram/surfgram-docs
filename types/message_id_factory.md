# MessageIdsFactory

Factory for creating and managing MessageId handlers.

## Usage

The factory automatically registers all active MessageId handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a MessageId handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_message_id`
- **Signature**: `@classmethod def register_message_id(cls, message_id_cls: Type["MessageId"]) -> None`
- **Description**: Registers a new MessageId handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["MessageId"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
