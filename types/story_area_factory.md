# StoryAreasFactory

Factory for creating and managing StoryArea handlers.

## Usage

The factory automatically registers all active StoryArea handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a StoryArea handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_story_area`
- **Signature**: `@classmethod def register_story_area(cls, story_area_cls: Type["StoryArea"]) -> None`
- **Description**: Registers a new StoryArea handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["StoryArea"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
