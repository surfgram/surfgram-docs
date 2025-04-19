# UserProfilePhotosFactory

Factory for creating and managing UserProfilePhotos handlers.

## Usage

The factory automatically registers all active UserProfilePhotos handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a UserProfilePhotos handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_user_profile_photos`
- **Signature**: `@classmethod def register_user_profile_photos(cls, user_profile_photos_cls: Type["UserProfilePhotos"]) -> None`
- **Description**: Registers a new UserProfilePhotos handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["UserProfilePhotos"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
