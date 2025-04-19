# MessageEntitiesFactory

Factory for creating and managing MessageEntity handlers.

## Usage

The factory automatically registers all active MessageEntity handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a MessageEntity handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_message_entity`
- **Signature**: `@classmethod def register_message_entity(cls, message_entity_cls: Type["MessageEntity"]) -> None`
- **Description**: Registers a new MessageEntity handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["MessageEntity"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
