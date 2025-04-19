# DiceFactory

Factory for creating and managing Dice handlers.

## Usage

The factory automatically registers all active Dice handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a Dice handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_dice`
- **Signature**: `@classmethod def register_dice(cls, dice_cls: Type["Dice"]) -> None`
- **Description**: Registers a new Dice handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["Dice"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
