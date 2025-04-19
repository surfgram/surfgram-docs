# VideoChatEndedsFactory

Factory for creating and managing VideoChatEnded handlers.

## Usage

The factory automatically registers all active VideoChatEnded handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a VideoChatEnded handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_video_chat_ended`
- **Signature**: `@classmethod def register_video_chat_ended(cls, video_chat_ended_cls: Type["VideoChatEnded"]) -> None`
- **Description**: Registers a new VideoChatEnded handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["VideoChatEnded"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
