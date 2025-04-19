# RevenueWithdrawalStateFailedsFactory

Factory for creating and managing RevenueWithdrawalStateFailed handlers.

## Usage

The factory automatically registers all active RevenueWithdrawalStateFailed handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a RevenueWithdrawalStateFailed handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_revenue_withdrawal_state_failed`
- **Signature**: `@classmethod def register_revenue_withdrawal_state_failed(cls, revenue_withdrawal_state_failed_cls: Type["RevenueWithdrawalStateFailed"]) -> None`
- **Description**: Registers a new RevenueWithdrawalStateFailed handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["RevenueWithdrawalStateFailed"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
