# ForumTopicEdited Handler

Telegram Bot API ForumTopicEdited type

## Usage

To create a ForumTopicEdited handler, you need to:

1. Create a class inheriting from `ForumTopicEdited`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import ForumTopicEdited
from typing import Callable


class ExampleForumTopicEdited(ForumTopicEdited):
    """Custom handler for ForumTopicEdited events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_forum_topic_edited"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the ForumTopicEdited event"""
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
    """Processes the ForumTopicEdited event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `name` (str): Optional. New name of the topic, if it was edited
- `icon_custom_emoji_id` (str): Optional. New identifier of the custom emoji shown as the topic icon, if it was edited; an empty string if the icon was removed
