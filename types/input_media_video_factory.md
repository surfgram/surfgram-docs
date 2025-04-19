# InputMediaVideosFactory

Factory for creating and managing InputMediaVideo handlers.

## Usage

The factory automatically registers all active InputMediaVideo handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InputMediaVideo handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_input_media_video`
- **Signature**: `@classmethod def register_input_media_video(cls, input_media_video_cls: Type["InputMediaVideo"]) -> None`
- **Description**: Registers a new InputMediaVideo handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InputMediaVideo"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
