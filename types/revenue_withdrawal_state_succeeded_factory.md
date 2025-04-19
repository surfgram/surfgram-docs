# RevenueWithdrawalStateSucceededsFactory

Factory for creating and managing RevenueWithdrawalStateSucceeded handlers.

## Usage

The factory automatically registers all active RevenueWithdrawalStateSucceeded handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a RevenueWithdrawalStateSucceeded handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_revenue_withdrawal_state_succeeded`
- **Signature**: `@classmethod def register_revenue_withdrawal_state_succeeded(cls, revenue_withdrawal_state_succeeded_cls: Type["RevenueWithdrawalStateSucceeded"]) -> None`
- **Description**: Registers a new RevenueWithdrawalStateSucceeded handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["RevenueWithdrawalStateSucceeded"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
