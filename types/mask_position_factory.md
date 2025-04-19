# MaskPositionsFactory

Factory for creating and managing MaskPosition handlers.

## Usage

The factory automatically registers all active MaskPosition handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a MaskPosition handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_mask_position`
- **Signature**: `@classmethod def register_mask_position(cls, mask_position_cls: Type["MaskPosition"]) -> None`
- **Description**: Registers a new MaskPosition handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["MaskPosition"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
