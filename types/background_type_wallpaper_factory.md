# BackgroundTypeWallpapersFactory

Factory for creating and managing BackgroundTypeWallpaper handlers.

## Usage

The factory automatically registers all active BackgroundTypeWallpaper handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a BackgroundTypeWallpaper handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_background_type_wallpaper`
- **Signature**: `@classmethod def register_background_type_wallpaper(cls, background_type_wallpaper_cls: Type["BackgroundTypeWallpaper"]) -> None`
- **Description**: Registers a new BackgroundTypeWallpaper handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["BackgroundTypeWallpaper"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
