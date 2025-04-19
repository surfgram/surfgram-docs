# MessageReactionCountUpdatedsFactory

Factory for creating and managing MessageReactionCountUpdated handlers.

## Usage

The factory automatically registers all active MessageReactionCountUpdated handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a MessageReactionCountUpdated handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_message_reaction_count_updated`
- **Signature**: `@classmethod def register_message_reaction_count_updated(cls, message_reaction_count_updated_cls: Type["MessageReactionCountUpdated"]) -> None`
- **Description**: Registers a new MessageReactionCountUpdated handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["MessageReactionCountUpdated"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
