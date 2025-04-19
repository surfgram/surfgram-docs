# ReactionTypeCustomEmojisFactory

Factory for creating and managing ReactionTypeCustomEmoji handlers.

## Usage

The factory automatically registers all active ReactionTypeCustomEmoji handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ReactionTypeCustomEmoji handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_reaction_type_custom_emoji`
- **Signature**: `@classmethod def register_reaction_type_custom_emoji(cls, reaction_type_custom_emoji_cls: Type["ReactionTypeCustomEmoji"]) -> None`
- **Description**: Registers a new ReactionTypeCustomEmoji handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ReactionTypeCustomEmoji"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
