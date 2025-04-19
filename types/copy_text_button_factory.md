# CopyTextButtonsFactory

Factory for creating and managing CopyTextButton handlers.

## Usage

The factory automatically registers all active CopyTextButton handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a CopyTextButton handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_copy_text_button`
- **Signature**: `@classmethod def register_copy_text_button(cls, copy_text_button_cls: Type["CopyTextButton"]) -> None`
- **Description**: Registers a new CopyTextButton handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["CopyTextButton"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
