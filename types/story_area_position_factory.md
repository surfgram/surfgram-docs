# StoryAreaPositionsFactory

Factory for creating and managing StoryAreaPosition handlers.

## Usage

The factory automatically registers all active StoryAreaPosition handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a StoryAreaPosition handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_story_area_position`
- **Signature**: `@classmethod def register_story_area_position(cls, story_area_position_cls: Type["StoryAreaPosition"]) -> None`
- **Description**: Registers a new StoryAreaPosition handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["StoryAreaPosition"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
