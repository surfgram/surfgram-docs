# LoginUrlsFactory

Factory for creating and managing LoginUrl handlers.

## Usage

The factory automatically registers all active LoginUrl handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a LoginUrl handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_login_url`
- **Signature**: `@classmethod def register_login_url(cls, login_url_cls: Type["LoginUrl"]) -> None`
- **Description**: Registers a new LoginUrl handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["LoginUrl"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
