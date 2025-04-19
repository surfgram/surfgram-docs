# AffiliateInfosFactory

Factory for creating and managing AffiliateInfo handlers.

## Usage

The factory automatically registers all active AffiliateInfo handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a AffiliateInfo handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_affiliate_info`
- **Signature**: `@classmethod def register_affiliate_info(cls, affiliate_info_cls: Type["AffiliateInfo"]) -> None`
- **Description**: Registers a new AffiliateInfo handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["AffiliateInfo"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
