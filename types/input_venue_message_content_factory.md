# InputVenueMessageContentsFactory

Factory for creating and managing InputVenueMessageContent handlers.

## Usage

The factory automatically registers all active InputVenueMessageContent handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InputVenueMessageContent handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_input_venue_message_content`
- **Signature**: `@classmethod def register_input_venue_message_content(cls, input_venue_message_content_cls: Type["InputVenueMessageContent"]) -> None`
- **Description**: Registers a new InputVenueMessageContent handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InputVenueMessageContent"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
