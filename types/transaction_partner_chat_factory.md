# TransactionPartnerChatsFactory

Factory for creating and managing TransactionPartnerChat handlers.

## Usage

The factory automatically registers all active TransactionPartnerChat handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a TransactionPartnerChat handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_transaction_partner_chat`
- **Signature**: `@classmethod def register_transaction_partner_chat(cls, transaction_partner_chat_cls: Type["TransactionPartnerChat"]) -> None`
- **Description**: Registers a new TransactionPartnerChat handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["TransactionPartnerChat"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
