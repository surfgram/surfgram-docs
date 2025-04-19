# ChosenInlineResultsFactory

Factory for creating and managing ChosenInlineResult handlers.

## Usage

The factory automatically registers all active ChosenInlineResult handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ChosenInlineResult handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_chosen_inline_result`
- **Signature**: `@classmethod def register_chosen_inline_result(cls, chosen_inline_result_cls: Type["ChosenInlineResult"]) -> None`
- **Description**: Registers a new ChosenInlineResult handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ChosenInlineResult"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
