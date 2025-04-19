# LoginUrl Handler

Telegram Bot API LoginUrl type

## Usage

To create a LoginUrl handler, you need to:

1. Create a class inheriting from `LoginUrl`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import LoginUrl
from typing import Callable


class ExampleLoginUrl(LoginUrl):
    """Custom handler for LoginUrl events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_login_url"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the LoginUrl event"""
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
    """Processes the LoginUrl event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `url` (str): An HTTPS URL to be opened with user authorization data added to the query string when the button is pressed. If the user refuses to provide authorization data, the original URL without information about the user will be opened. The data added is the same as described in Receiving authorization data.NOTE: You must always check the hash of the received data to verify the authentication and the integrity of the data as described in Checking authorization.
- `forward_text` (str): Optional. New text of the button in forwarded messages.
- `bot_username` (str): Optional. Username of a bot, which will be used for user authorization. See Setting up a bot for more details. If not specified, the current bot's username will be assumed. The url's domain must be the same as the domain linked with the bot. See Linking your domain to the bot for more details.
- `request_write_access` (bool): Optional. Pass True to request the permission for your bot to send messages to the user.
