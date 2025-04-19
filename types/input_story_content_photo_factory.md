# InputStoryContentPhotosFactory

Factory for creating and managing InputStoryContentPhoto handlers.

## Usage

The factory automatically registers all active InputStoryContentPhoto handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InputStoryContentPhoto handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_input_story_content_photo`
- **Signature**: `@classmethod def register_input_story_content_photo(cls, input_story_content_photo_cls: Type["InputStoryContentPhoto"]) -> None`
- **Description**: Registers a new InputStoryContentPhoto handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InputStoryContentPhoto"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
