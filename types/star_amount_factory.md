# StarAmountsFactory

Factory for creating and managing StarAmount handlers.

## Usage

The factory automatically registers all active StarAmount handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a StarAmount handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_star_amount`
- **Signature**: `@classmethod def register_star_amount(cls, star_amount_cls: Type["StarAmount"]) -> None`
- **Description**: Registers a new StarAmount handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["StarAmount"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
