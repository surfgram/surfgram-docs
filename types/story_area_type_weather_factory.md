# StoryAreaTypeWeathersFactory

Factory for creating and managing StoryAreaTypeWeather handlers.

## Usage

The factory automatically registers all active StoryAreaTypeWeather handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a StoryAreaTypeWeather handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_story_area_type_weather`
- **Signature**: `@classmethod def register_story_area_type_weather(cls, story_area_type_weather_cls: Type["StoryAreaTypeWeather"]) -> None`
- **Description**: Registers a new StoryAreaTypeWeather handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["StoryAreaTypeWeather"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
