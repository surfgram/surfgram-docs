# BackgroundTypeChatThemesFactory

Factory for creating and managing BackgroundTypeChatTheme handlers.

## Usage

The factory automatically registers all active BackgroundTypeChatTheme handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a BackgroundTypeChatTheme handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_background_type_chat_theme`
- **Signature**: `@classmethod def register_background_type_chat_theme(cls, background_type_chat_theme_cls: Type["BackgroundTypeChatTheme"]) -> None`
- **Description**: Registers a new BackgroundTypeChatTheme handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["BackgroundTypeChatTheme"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
