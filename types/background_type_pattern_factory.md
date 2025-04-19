# BackgroundTypePatternsFactory

Factory for creating and managing BackgroundTypePattern handlers.

## Usage

The factory automatically registers all active BackgroundTypePattern handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a BackgroundTypePattern handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_background_type_pattern`
- **Signature**: `@classmethod def register_background_type_pattern(cls, background_type_pattern_cls: Type["BackgroundTypePattern"]) -> None`
- **Description**: Registers a new BackgroundTypePattern handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["BackgroundTypePattern"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
