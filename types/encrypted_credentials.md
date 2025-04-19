# EncryptedCredentials Handler

Telegram Bot API EncryptedCredentials type

## Usage

To create a EncryptedCredentials handler, you need to:

1. Create a class inheriting from `EncryptedCredentials`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import EncryptedCredentials
from typing import Callable


class ExampleEncryptedCredentials(EncryptedCredentials):
    """Custom handler for EncryptedCredentials events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_encrypted_credentials"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the EncryptedCredentials event"""
        # Your implementation here
        pass
```

## Required Properties

### `__names__`
- **Type**: `List[str]`
- **Description**: List of trigger names that will activate this handler
- **Example**: `return ["start", "begin"]`

### `__callback__`
- **Type**: `Callable`
- **Description**: Returns the async function that will process the event
- **Signature**: `async def callback(update, bot) -> None`

## Handler Method

Your handler method should have the following signature:

```python
async def handle(self, update, bot):
    """Processes the EncryptedCredentials event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `data` (str): Base64-encoded encrypted JSON-serialized data with unique user's payload, data hashes and secrets required for EncryptedPassportElement decryption and authentication
- `hash` (str): Base64-encoded data hash for data authentication
- `secret` (str): Base64-encoded secret, encrypted with the bot's public RSA key, required for data decryption
