# ChatFullInfosFactory

Factory for creating and managing ChatFullInfo handlers.

## Usage

The factory automatically registers all active ChatFullInfo handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ChatFullInfo handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_chat_full_info`
- **Signature**: `@classmethod def register_chat_full_info(cls, chat_full_info_cls: Type["ChatFullInfo"]) -> None`
- **Description**: Registers a new ChatFullInfo handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ChatFullInfo"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
