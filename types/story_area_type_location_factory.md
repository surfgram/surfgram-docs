# StoryAreaTypeLocationsFactory

Factory for creating and managing StoryAreaTypeLocation handlers.

## Usage

The factory automatically registers all active StoryAreaTypeLocation handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a StoryAreaTypeLocation handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_story_area_type_location`
- **Signature**: `@classmethod def register_story_area_type_location(cls, story_area_type_location_cls: Type["StoryAreaTypeLocation"]) -> None`
- **Description**: Registers a new StoryAreaTypeLocation handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["StoryAreaTypeLocation"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
