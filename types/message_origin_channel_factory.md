# MessageOriginChannelsFactory

Factory for creating and managing MessageOriginChannel handlers.

## Usage

The factory automatically registers all active MessageOriginChannel handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a MessageOriginChannel handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_message_origin_channel`
- **Signature**: `@classmethod def register_message_origin_channel(cls, message_origin_channel_cls: Type["MessageOriginChannel"]) -> None`
- **Description**: Registers a new MessageOriginChannel handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["MessageOriginChannel"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
