# InputProfilePhotoAnimatedsFactory

Factory for creating and managing InputProfilePhotoAnimated handlers.

## Usage

The factory automatically registers all active InputProfilePhotoAnimated handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InputProfilePhotoAnimated handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_input_profile_photo_animated`
- **Signature**: `@classmethod def register_input_profile_photo_animated(cls, input_profile_photo_animated_cls: Type["InputProfilePhotoAnimated"]) -> None`
- **Description**: Registers a new InputProfilePhotoAnimated handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InputProfilePhotoAnimated"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
