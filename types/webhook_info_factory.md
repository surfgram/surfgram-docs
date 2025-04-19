# WebhookInfosFactory

Factory for creating and managing WebhookInfo handlers.

## Usage

The factory automatically registers all active WebhookInfo handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a WebhookInfo handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_webhook_info`
- **Signature**: `@classmethod def register_webhook_info(cls, webhook_info_cls: Type["WebhookInfo"]) -> None`
- **Description**: Registers a new WebhookInfo handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["WebhookInfo"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
