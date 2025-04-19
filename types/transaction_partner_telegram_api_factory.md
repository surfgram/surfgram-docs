# TransactionPartnerTelegramApisFactory

Factory for creating and managing TransactionPartnerTelegramApi handlers.

## Usage

The factory automatically registers all active TransactionPartnerTelegramApi handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a TransactionPartnerTelegramApi handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_transaction_partner_telegram_api`
- **Signature**: `@classmethod def register_transaction_partner_telegram_api(cls, transaction_partner_telegram_api_cls: Type["TransactionPartnerTelegramApi"]) -> None`
- **Description**: Registers a new TransactionPartnerTelegramApi handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["TransactionPartnerTelegramApi"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
