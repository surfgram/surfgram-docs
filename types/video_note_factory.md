# VideoNotesFactory

Factory for creating and managing VideoNote handlers.

## Usage

The factory automatically registers all active VideoNote handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a VideoNote handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_video_note`
- **Signature**: `@classmethod def register_video_note(cls, video_note_cls: Type["VideoNote"]) -> None`
- **Description**: Registers a new VideoNote handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["VideoNote"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
