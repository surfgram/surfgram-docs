# AcceptedGiftTypesFactory

Factory for creating and managing AcceptedGiftTypes handlers.

## Usage

The factory automatically registers all active AcceptedGiftTypes handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a AcceptedGiftTypes handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_accepted_gift_types`
- **Signature**: `@classmethod def register_accepted_gift_types(cls, accepted_gift_types_cls: Type["AcceptedGiftTypes"]) -> None`
- **Description**: Registers a new AcceptedGiftTypes handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["AcceptedGiftTypes"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
