# TransactionPartnerAffiliateProgramsFactory

Factory for creating and managing TransactionPartnerAffiliateProgram handlers.

## Usage

The factory automatically registers all active TransactionPartnerAffiliateProgram handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a TransactionPartnerAffiliateProgram handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_transaction_partner_affiliate_program`
- **Signature**: `@classmethod def register_transaction_partner_affiliate_program(cls, transaction_partner_affiliate_program_cls: Type["TransactionPartnerAffiliateProgram"]) -> None`
- **Description**: Registers a new TransactionPartnerAffiliateProgram handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["TransactionPartnerAffiliateProgram"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
