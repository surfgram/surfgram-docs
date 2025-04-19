# TransactionPartnerUsersFactory

Factory for creating and managing TransactionPartnerUser handlers.

## Usage

The factory automatically registers all active TransactionPartnerUser handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a TransactionPartnerUser handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_transaction_partner_user`
- **Signature**: `@classmethod def register_transaction_partner_user(cls, transaction_partner_user_cls: Type["TransactionPartnerUser"]) -> None`
- **Description**: Registers a new TransactionPartnerUser handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["TransactionPartnerUser"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
