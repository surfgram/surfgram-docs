# PollsFactory

Factory for creating and managing Poll handlers.

## Usage

The factory automatically registers all active Poll handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a Poll handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_poll`
- **Signature**: `@classmethod def register_poll(cls, poll_cls: Type["Poll"]) -> None`
- **Description**: Registers a new Poll handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["Poll"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
