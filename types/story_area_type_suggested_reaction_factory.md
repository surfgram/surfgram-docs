# StoryAreaTypeSuggestedReactionsFactory

Factory for creating and managing StoryAreaTypeSuggestedReaction handlers.

## Usage

The factory automatically registers all active StoryAreaTypeSuggestedReaction handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a StoryAreaTypeSuggestedReaction handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_story_area_type_suggested_reaction`
- **Signature**: `@classmethod def register_story_area_type_suggested_reaction(cls, story_area_type_suggested_reaction_cls: Type["StoryAreaTypeSuggestedReaction"]) -> None`
- **Description**: Registers a new StoryAreaTypeSuggestedReaction handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["StoryAreaTypeSuggestedReaction"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
