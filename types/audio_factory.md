# AudioFactory

Factory for creating and managing Audio handlers.

## Usage

The factory automatically registers all active Audio handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a Audio handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_audio`
- **Signature**: `@classmethod def register_audio(cls, audio_cls: Type["Audio"]) -> None`
- **Description**: Registers a new Audio handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["Audio"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
