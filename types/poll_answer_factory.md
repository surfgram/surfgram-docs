# PollAnswersFactory

Factory for creating and managing PollAnswer handlers.

## Usage

The factory automatically registers all active PollAnswer handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a PollAnswer handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_poll_answer`
- **Signature**: `@classmethod def register_poll_answer(cls, poll_answer_cls: Type["PollAnswer"]) -> None`
- **Description**: Registers a new PollAnswer handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["PollAnswer"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
