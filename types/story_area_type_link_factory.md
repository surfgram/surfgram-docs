# StoryAreaTypeLinksFactory

Factory for creating and managing StoryAreaTypeLink handlers.

## Usage

The factory automatically registers all active StoryAreaTypeLink handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a StoryAreaTypeLink handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_story_area_type_link`
- **Signature**: `@classmethod def register_story_area_type_link(cls, story_area_type_link_cls: Type["StoryAreaTypeLink"]) -> None`
- **Description**: Registers a new StoryAreaTypeLink handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["StoryAreaTypeLink"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
