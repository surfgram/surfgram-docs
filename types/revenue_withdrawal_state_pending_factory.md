# RevenueWithdrawalStatePendingsFactory

Factory for creating and managing RevenueWithdrawalStatePending handlers.

## Usage

The factory automatically registers all active RevenueWithdrawalStatePending handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a RevenueWithdrawalStatePending handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_revenue_withdrawal_state_pending`
- **Signature**: `@classmethod def register_revenue_withdrawal_state_pending(cls, revenue_withdrawal_state_pending_cls: Type["RevenueWithdrawalStatePending"]) -> None`
- **Description**: Registers a new RevenueWithdrawalStatePending handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["RevenueWithdrawalStatePending"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
