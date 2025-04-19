# InvoicesFactory

Factory for creating and managing Invoice handlers.

## Usage

The factory automatically registers all active Invoice handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a Invoice handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_invoice`
- **Signature**: `@classmethod def register_invoice(cls, invoice_cls: Type["Invoice"]) -> None`
- **Description**: Registers a new Invoice handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["Invoice"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
