# InputMediaAudiosFactory

Factory for creating and managing InputMediaAudio handlers.

## Usage

The factory automatically registers all active InputMediaAudio handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InputMediaAudio handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_input_media_audio`
- **Signature**: `@classmethod def register_input_media_audio(cls, input_media_audio_cls: Type["InputMediaAudio"]) -> None`
- **Description**: Registers a new InputMediaAudio handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InputMediaAudio"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
