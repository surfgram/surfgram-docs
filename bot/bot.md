# Bot

The core component of the Surfgram framework that handles all Telegram Bot API interactions and update processing.

## Key Responsibilities
- Manages bot authentication and session
- Provides interface to Telegram Bot API
- Handles incoming updates
- Routes updates to appropriate handlers

## Core Features

### Dynamic API Access
Call any Telegram Bot API method directly as bot methods:

```python
# Send message
await bot.send_message(
    chat_id=12345,
    text="Hello from Surfgram!"
)

# Get user profile photos
photos = await bot.get_user_profile_photos(user_id=12345)
```

### Update Processing Pipeline
1. Receives updates via long polling
2. Converts to `APIObject` instances
3. Routes to registered handlers
4. Maintains update offset

### Built-in Error Handling
- Automatic token validation
- API error detection
- Debug logging support

## Initialization

```python
from surfgram.core.bot import Bot
from config import BotConfig  # Your config class

bot = Bot(config=BotConfig, debug_mode=True)
```

## Common Usage Patterns

### 1. Sending API Requests
```python
# Send photo
await bot.send_photo(
    chat_id=update.message.chat.id,
    photo=open('image.jpg', 'rb')
)

# Edit message
await bot.edit_message_text(
    chat_id=chat_id,
    message_id=msg_id,
    text="Updated text"
)
```

### 2. Handling Updates
```python
class MessageLogger(Listener):
    async def on_update(self, update):
        print(f"New update: {update}")
        await super().on_update(update)  # Continue normal processing
```

### 3. Custom API Wrappers
```python
async def send_hello(bot, chat_id):
    await bot.send_message(
        chat_id=chat_id,
        text="Hello!"
    )
```

## Advanced Configuration
- Set custom `offset` and `timeout` in listener
- Override request handling in `_make_request`
- Extend with custom middleware

## Best Practices
- Initialize once per application
- Reuse bot instance across handlers
- Access through dependency injection
- Wrap in context managers for resource cleanup
