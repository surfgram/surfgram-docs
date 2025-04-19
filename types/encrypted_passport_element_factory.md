# EncryptedPassportElementsFactory

Factory for creating and managing EncryptedPassportElement handlers.

## Usage

The factory automatically registers all active EncryptedPassportElement handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a EncryptedPassportElement handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_encrypted_passport_element`
- **Signature**: `@classmethod def register_encrypted_passport_element(cls, encrypted_passport_element_cls: Type["EncryptedPassportElement"]) -> None`
- **Description**: Registers a new EncryptedPassportElement handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["EncryptedPassportElement"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
