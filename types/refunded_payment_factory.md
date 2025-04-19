# RefundedPaymentsFactory

Factory for creating and managing RefundedPayment handlers.

## Usage

The factory automatically registers all active RefundedPayment handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a RefundedPayment handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_refunded_payment`
- **Signature**: `@classmethod def register_refunded_payment(cls, refunded_payment_cls: Type["RefundedPayment"]) -> None`
- **Description**: Registers a new RefundedPayment handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["RefundedPayment"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
