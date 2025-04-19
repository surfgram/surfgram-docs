# ResponseParametersFactory

Factory for creating and managing ResponseParameters handlers.

## Usage

The factory automatically registers all active ResponseParameters handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ResponseParameters handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_response_parameters`
- **Signature**: `@classmethod def register_response_parameters(cls, response_parameters_cls: Type["ResponseParameters"]) -> None`
- **Description**: Registers a new ResponseParameters handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ResponseParameters"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
