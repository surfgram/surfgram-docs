# StarTransactionsFactory

Factory for creating and managing StarTransaction handlers.

## Usage

The factory automatically registers all active StarTransaction handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a StarTransaction handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_star_transaction`
- **Signature**: `@classmethod def register_star_transaction(cls, star_transaction_cls: Type["StarTransaction"]) -> None`
- **Description**: Registers a new StarTransaction handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["StarTransaction"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
