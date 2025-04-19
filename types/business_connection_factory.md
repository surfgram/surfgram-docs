# BusinessConnectionsFactory

Factory for creating and managing BusinessConnection handlers.

## Usage

The factory automatically registers all active BusinessConnection handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a BusinessConnection handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_business_connection`
- **Signature**: `@classmethod def register_business_connection(cls, business_connection_cls: Type["BusinessConnection"]) -> None`
- **Description**: Registers a new BusinessConnection handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["BusinessConnection"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
