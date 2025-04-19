# ChatLocationsFactory

Factory for creating and managing ChatLocation handlers.

## Usage

The factory automatically registers all active ChatLocation handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ChatLocation handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_chat_location`
- **Signature**: `@classmethod def register_chat_location(cls, chat_location_cls: Type["ChatLocation"]) -> None`
- **Description**: Registers a new ChatLocation handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ChatLocation"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
