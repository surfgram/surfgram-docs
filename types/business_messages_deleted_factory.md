# BusinessMessagesDeletedsFactory

Factory for creating and managing BusinessMessagesDeleted handlers.

## Usage

The factory automatically registers all active BusinessMessagesDeleted handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a BusinessMessagesDeleted handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_business_messages_deleted`
- **Signature**: `@classmethod def register_business_messages_deleted(cls, business_messages_deleted_cls: Type["BusinessMessagesDeleted"]) -> None`
- **Description**: Registers a new BusinessMessagesDeleted handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["BusinessMessagesDeleted"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
