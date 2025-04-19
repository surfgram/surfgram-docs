# SwitchInlineQueryChosenChatsFactory

Factory for creating and managing SwitchInlineQueryChosenChat handlers.

## Usage

The factory automatically registers all active SwitchInlineQueryChosenChat handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a SwitchInlineQueryChosenChat handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_switch_inline_query_chosen_chat`
- **Signature**: `@classmethod def register_switch_inline_query_chosen_chat(cls, switch_inline_query_chosen_chat_cls: Type["SwitchInlineQueryChosenChat"]) -> None`
- **Description**: Registers a new SwitchInlineQueryChosenChat handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["SwitchInlineQueryChosenChat"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
