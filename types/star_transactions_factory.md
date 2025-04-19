# StarTransactionsFactory

Factory for creating and managing StarTransactions handlers.

## Usage

The factory automatically registers all active StarTransactions handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a StarTransactions handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_star_transactions`
- **Signature**: `@classmethod def register_star_transactions(cls, star_transactions_cls: Type["StarTransactions"]) -> None`
- **Description**: Registers a new StarTransactions handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["StarTransactions"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
