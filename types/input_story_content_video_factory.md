# InputStoryContentVideosFactory

Factory for creating and managing InputStoryContentVideo handlers.

## Usage

The factory automatically registers all active InputStoryContentVideo handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InputStoryContentVideo handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_input_story_content_video`
- **Signature**: `@classmethod def register_input_story_content_video(cls, input_story_content_video_cls: Type["InputStoryContentVideo"]) -> None`
- **Description**: Registers a new InputStoryContentVideo handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InputStoryContentVideo"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
