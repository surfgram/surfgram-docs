# TransactionPartnerFragmentsFactory

Factory for creating and managing TransactionPartnerFragment handlers.

## Usage

The factory automatically registers all active TransactionPartnerFragment handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a TransactionPartnerFragment handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_transaction_partner_fragment`
- **Signature**: `@classmethod def register_transaction_partner_fragment(cls, transaction_partner_fragment_cls: Type["TransactionPartnerFragment"]) -> None`
- **Description**: Registers a new TransactionPartnerFragment handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["TransactionPartnerFragment"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
