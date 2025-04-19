# InputPaidMediaVideosFactory

Factory for creating and managing InputPaidMediaVideo handlers.

## Usage

The factory automatically registers all active InputPaidMediaVideo handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InputPaidMediaVideo handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_input_paid_media_video`
- **Signature**: `@classmethod def register_input_paid_media_video(cls, input_paid_media_video_cls: Type["InputPaidMediaVideo"]) -> None`
- **Description**: Registers a new InputPaidMediaVideo handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InputPaidMediaVideo"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
