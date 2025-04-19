# ForumTopicsFactory

Factory for creating and managing ForumTopic handlers.

## Usage

The factory automatically registers all active ForumTopic handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ForumTopic handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_forum_topic`
- **Signature**: `@classmethod def register_forum_topic(cls, forum_topic_cls: Type["ForumTopic"]) -> None`
- **Description**: Registers a new ForumTopic handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ForumTopic"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
