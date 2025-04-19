# BusinessBotRightsFactory

Factory for creating and managing BusinessBotRights handlers.

## Usage

The factory automatically registers all active BusinessBotRights handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a BusinessBotRights handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_business_bot_rights`
- **Signature**: `@classmethod def register_business_bot_rights(cls, business_bot_rights_cls: Type["BusinessBotRights"]) -> None`
- **Description**: Registers a new BusinessBotRights handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["BusinessBotRights"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
