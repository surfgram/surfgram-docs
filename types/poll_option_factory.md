# PollOptionsFactory

Factory for creating and managing PollOption handlers.

## Usage

The factory automatically registers all active PollOption handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a PollOption handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_poll_option`
- **Signature**: `@classmethod def register_poll_option(cls, poll_option_cls: Type["PollOption"]) -> None`
- **Description**: Registers a new PollOption handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["PollOption"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
