# VideosFactory

Factory for creating and managing Video handlers.

## Usage

The factory automatically registers all active Video handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a Video handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_video`
- **Signature**: `@classmethod def register_video(cls, video_cls: Type["Video"]) -> None`
- **Description**: Registers a new Video handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["Video"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
