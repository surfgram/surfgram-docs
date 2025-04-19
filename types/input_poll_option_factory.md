# InputPollOptionsFactory

Factory for creating and managing InputPollOption handlers.

## Usage

The factory automatically registers all active InputPollOption handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InputPollOption handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_input_poll_option`
- **Signature**: `@classmethod def register_input_poll_option(cls, input_poll_option_cls: Type["InputPollOption"]) -> None`
- **Description**: Registers a new InputPollOption handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InputPollOption"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
