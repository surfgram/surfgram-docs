# ForumTopicCreatedsFactory

Factory for creating and managing ForumTopicCreated handlers.

## Usage

The factory automatically registers all active ForumTopicCreated handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ForumTopicCreated handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_forum_topic_created`
- **Signature**: `@classmethod def register_forum_topic_created(cls, forum_topic_created_cls: Type["ForumTopicCreated"]) -> None`
- **Description**: Registers a new ForumTopicCreated handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ForumTopicCreated"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
