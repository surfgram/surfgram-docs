# BusinessIntrosFactory

Factory for creating and managing BusinessIntro handlers.

## Usage

The factory automatically registers all active BusinessIntro handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a BusinessIntro handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_business_intro`
- **Signature**: `@classmethod def register_business_intro(cls, business_intro_cls: Type["BusinessIntro"]) -> None`
- **Description**: Registers a new BusinessIntro handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["BusinessIntro"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
