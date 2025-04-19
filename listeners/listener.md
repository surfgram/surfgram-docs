# Listener

Abstract base class for handling Telegram bot updates

## Interface Definition

```python
class Listener(ABC):
    @abstractmethod
    async def on_update(self, update: APIObject) -> None: ...
```

## Usage

Implement this interface to create custom update handlers:

```python
class MyListener(Listener):
    async def on_update(self, update: APIObject) -> None:
        print(f"Received update: {update}")
        # Your update processing logic here
```

## Key Features

- **Asynchronous** processing (`async` method)
- Receives updates as `APIObject` instances
- Must be implemented by concrete handler classes
- Core component of the bot's event system

## Implementation Requirements

1. Subclass `Listener`
2. Implement `on_update` method
3. Handle incoming updates (messages, callbacks, etc.)

## Example Use Case

```python
class MessageLogger(Listener):
    async def on_update(self, update: APIObject) -> None:
        if hasattr(update, 'message'):
            print(f"New message: {update.message.text}")
```

> Note: This is a public interface for creating custom bot update handlers.