# ReplyParametersFactory

Factory for creating and managing ReplyParameters handlers.

## Usage

The factory automatically registers all active ReplyParameters handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ReplyParameters handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_reply_parameters`
- **Signature**: `@classmethod def register_reply_parameters(cls, reply_parameters_cls: Type["ReplyParameters"]) -> None`
- **Description**: Registers a new ReplyParameters handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ReplyParameters"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
