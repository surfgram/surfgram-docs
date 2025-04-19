# ChatAdministratorRightsFactory

Factory for creating and managing ChatAdministratorRights handlers.

## Usage

The factory automatically registers all active ChatAdministratorRights handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ChatAdministratorRights handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_chat_administrator_rights`
- **Signature**: `@classmethod def register_chat_administrator_rights(cls, chat_administrator_rights_cls: Type["ChatAdministratorRights"]) -> None`
- **Description**: Registers a new ChatAdministratorRights handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ChatAdministratorRights"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
