# StoryAreaTypeUniqueGiftsFactory

Factory for creating and managing StoryAreaTypeUniqueGift handlers.

## Usage

The factory automatically registers all active StoryAreaTypeUniqueGift handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a StoryAreaTypeUniqueGift handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_story_area_type_unique_gift`
- **Signature**: `@classmethod def register_story_area_type_unique_gift(cls, story_area_type_unique_gift_cls: Type["StoryAreaTypeUniqueGift"]) -> None`
- **Description**: Registers a new StoryAreaTypeUniqueGift handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["StoryAreaTypeUniqueGift"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
