# PaidMediaPurchasedsFactory

Factory for creating and managing PaidMediaPurchased handlers.

## Usage

The factory automatically registers all active PaidMediaPurchased handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a PaidMediaPurchased handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_paid_media_purchased`
- **Signature**: `@classmethod def register_paid_media_purchased(cls, paid_media_purchased_cls: Type["PaidMediaPurchased"]) -> None`
- **Description**: Registers a new PaidMediaPurchased handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["PaidMediaPurchased"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
