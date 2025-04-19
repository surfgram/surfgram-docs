# GameHighScoresFactory

Factory for creating and managing GameHighScore handlers.

## Usage

The factory automatically registers all active GameHighScore handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a GameHighScore handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_game_high_score`
- **Signature**: `@classmethod def register_game_high_score(cls, game_high_score_cls: Type["GameHighScore"]) -> None`
- **Description**: Registers a new GameHighScore handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["GameHighScore"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
