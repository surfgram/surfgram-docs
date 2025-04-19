# ReactionCountsFactory

Factory for creating and managing ReactionCount handlers.

## Usage

The factory automatically registers all active ReactionCount handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ReactionCount handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_reaction_count`
- **Signature**: `@classmethod def register_reaction_count(cls, reaction_count_cls: Type["ReactionCount"]) -> None`
- **Description**: Registers a new ReactionCount handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ReactionCount"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
