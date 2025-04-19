# EncryptedCredentialsFactory

Factory for creating and managing EncryptedCredentials handlers.

## Usage

The factory automatically registers all active EncryptedCredentials handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a EncryptedCredentials handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_encrypted_credentials`
- **Signature**: `@classmethod def register_encrypted_credentials(cls, encrypted_credentials_cls: Type["EncryptedCredentials"]) -> None`
- **Description**: Registers a new EncryptedCredentials handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["EncryptedCredentials"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
