# ForumTopicEditedsFactory

Factory for creating and managing ForumTopicEdited handlers.

## Usage

The factory automatically registers all active ForumTopicEdited handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ForumTopicEdited handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_forum_topic_edited`
- **Signature**: `@classmethod def register_forum_topic_edited(cls, forum_topic_edited_cls: Type["ForumTopicEdited"]) -> None`
- **Description**: Registers a new ForumTopicEdited handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ForumTopicEdited"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
