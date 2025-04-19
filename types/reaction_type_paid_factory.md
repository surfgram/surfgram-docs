# ReactionTypePaidsFactory

Factory for creating and managing ReactionTypePaid handlers.

## Usage

The factory automatically registers all active ReactionTypePaid handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ReactionTypePaid handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_reaction_type_paid`
- **Signature**: `@classmethod def register_reaction_type_paid(cls, reaction_type_paid_cls: Type["ReactionTypePaid"]) -> None`
- **Description**: Registers a new ReactionTypePaid handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ReactionTypePaid"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
