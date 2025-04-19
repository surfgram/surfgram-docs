# SentWebAppMessagesFactory

Factory for creating and managing SentWebAppMessage handlers.

## Usage

The factory automatically registers all active SentWebAppMessage handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a SentWebAppMessage handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_sent_web_app_message`
- **Signature**: `@classmethod def register_sent_web_app_message(cls, sent_web_app_message_cls: Type["SentWebAppMessage"]) -> None`
- **Description**: Registers a new SentWebAppMessage handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["SentWebAppMessage"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
