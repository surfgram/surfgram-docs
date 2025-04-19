# UniqueGiftSymbolsFactory

Factory for creating and managing UniqueGiftSymbol handlers.

## Usage

The factory automatically registers all active UniqueGiftSymbol handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a UniqueGiftSymbol handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_unique_gift_symbol`
- **Signature**: `@classmethod def register_unique_gift_symbol(cls, unique_gift_symbol_cls: Type["UniqueGiftSymbol"]) -> None`
- **Description**: Registers a new UniqueGiftSymbol handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["UniqueGiftSymbol"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
