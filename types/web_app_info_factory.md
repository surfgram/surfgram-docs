# WebAppInfosFactory

Factory for creating and managing WebAppInfo handlers.

## Usage

The factory automatically registers all active WebAppInfo handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a WebAppInfo handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_web_app_info`
- **Signature**: `@classmethod def register_web_app_info(cls, web_app_info_cls: Type["WebAppInfo"]) -> None`
- **Description**: Registers a new WebAppInfo handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["WebAppInfo"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
