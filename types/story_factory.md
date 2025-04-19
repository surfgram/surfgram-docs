# StoriesFactory

Factory for creating and managing Story handlers.

## Usage

The factory automatically registers all active Story handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a Story handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_story`
- **Signature**: `@classmethod def register_story(cls, story_cls: Type["Story"]) -> None`
- **Description**: Registers a new Story handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["Story"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
