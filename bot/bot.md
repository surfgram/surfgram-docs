# Bot

## Package
```python
from surfgram import Bot
```

## Class Description
The `Bot` class provides a high-level interface for interacting with the Telegram Bot API, featuring dynamic method dispatch and configurable execution modes.

## Constructor
```python
Bot(config: BaseConfig, debug_mode: bool = False)
```

### Parameters
| Parameter   | Type       | Required | Default | Description |
|-------------|------------|----------|---------|-------------|
| `config`    | BaseConfig | Yes      | -       | Configuration object implementing `BaseConfig` interface |
| `debug_mode`| bool       | No       | False   | Enables verbose logging for debugging purposes |

### Configuration Requirements
The configuration object must implement all required parameters specified in the [Surfgram Configuration Documentation][https://github.com/surfgram/surfgram-docs/blob/main/structures/config.md]

## Public Interface

### Dynamic Method Dispatch
```python
__getattr__(method_name: str) -> Callable
```

#### Description
Provides dynamic access to all Telegram Bot API methods through Pythonic method calls.

#### Behavior
1. Translates method calls to corresponding Telegram API endpoints
2. Converts snake_case method names to camelCase API endpoints
3. Automatically formats request payloads

#### Example
```python
# Python method call
bot.send_message(chat_id=123, text="Test")

# Equivalent API request
POST /sendMessage
{
  "chat_id": 123,
  "text": "Test"
}
```

#### Supported Methods
All methods listed in the official [Telegram Bot API Documentation](https://core.telegram.org/bots/api) are supported.

### Event Processing
```python
listen() -> None
```

#### Description
Initiates the bot's event processing loop based on configured listener implementation.

#### Features
- Implements long-polling for update retrieval
- Processes updates through configured handler pipeline
- Maintains persistent connection to Telegram servers

#### Requirements
The configuration must include a properly initialized listener component. See [Listener Configuration Guide](https://github.com/surfgram/surfgram-docs/blob/main/listeners).

## Usage Example

```python
from surfgram import Bot
from config import Config

config = Config()
bot = Bot(config=config, debug_mode=True)

bot.send_message(
    chat_id=1337107725,
    text="Hello, world",
    parse_mode="MarkdownV2"
)

# Start event loop
bot.listen()
```
