# GamesFactory

Factory for creating and managing Game handlers.

## Usage

The factory automatically registers all active Game handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a Game handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_game`
- **Signature**: `@classmethod def register_game(cls, game_cls: Type["Game"]) -> None`
- **Description**: Registers a new Game handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["Game"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
