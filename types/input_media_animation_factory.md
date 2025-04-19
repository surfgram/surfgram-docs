# InputMediaAnimationsFactory

Factory for creating and managing InputMediaAnimation handlers.

## Usage

The factory automatically registers all active InputMediaAnimation handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InputMediaAnimation handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_input_media_animation`
- **Signature**: `@classmethod def register_input_media_animation(cls, input_media_animation_cls: Type["InputMediaAnimation"]) -> None`
- **Description**: Registers a new InputMediaAnimation handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InputMediaAnimation"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
