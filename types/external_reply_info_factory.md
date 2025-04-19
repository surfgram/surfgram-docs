# ExternalReplyInfosFactory

Factory for creating and managing ExternalReplyInfo handlers.

## Usage

The factory automatically registers all active ExternalReplyInfo handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ExternalReplyInfo handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_external_reply_info`
- **Signature**: `@classmethod def register_external_reply_info(cls, external_reply_info_cls: Type["ExternalReplyInfo"]) -> None`
- **Description**: Registers a new ExternalReplyInfo handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ExternalReplyInfo"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
