# Document Handler

Telegram Bot API Document type

## Usage

To create a Document handler, you need to:

1. Create a class inheriting from `Document`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import Document
from typing import Callable


class ExampleDocument(Document):
    """Custom handler for Document events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_document"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the Document event"""
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
    """Processes the Document event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `file_id` (str): Identifier for this file, which can be used to download or reuse the file
- `file_unique_id` (str): Unique identifier for this file, which is supposed to be the same over time and for different bots. Can't be used to download or reuse the file.
- `thumbnail` (PhotoSize): Optional. Document thumbnail as defined by the sender
- `file_name` (str): Optional. Original filename as defined by the sender
- `mime_type` (str): Optional. MIME type of the file as defined by the sender
- `file_size` (int): Optional. File size in bytes. It can be bigger than 2^31 and some programming languages may have difficulty/silent defects in interpreting it. But it has at most 52 significant bits, so a signed 64-bit integer or double-precision float type are safe for storing this value.
