# SuccessfulPaymentsFactory

Factory for creating and managing SuccessfulPayment handlers.

## Usage

The factory automatically registers all active SuccessfulPayment handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a SuccessfulPayment handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_successful_payment`
- **Signature**: `@classmethod def register_successful_payment(cls, successful_payment_cls: Type["SuccessfulPayment"]) -> None`
- **Description**: Registers a new SuccessfulPayment handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["SuccessfulPayment"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
