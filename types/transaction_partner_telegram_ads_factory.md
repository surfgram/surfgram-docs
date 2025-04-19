# TransactionPartnerTelegramAdsFactory

Factory for creating and managing TransactionPartnerTelegramAds handlers.

## Usage

The factory automatically registers all active TransactionPartnerTelegramAds handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a TransactionPartnerTelegramAds handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_transaction_partner_telegram_ads`
- **Signature**: `@classmethod def register_transaction_partner_telegram_ads(cls, transaction_partner_telegram_ads_cls: Type["TransactionPartnerTelegramAds"]) -> None`
- **Description**: Registers a new TransactionPartnerTelegramAds handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["TransactionPartnerTelegramAds"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
