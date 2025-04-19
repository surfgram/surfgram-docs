# StoryArea Handler

Telegram Bot API StoryArea type

## Usage

To create a StoryArea handler, you need to:

1. Create a class inheriting from `StoryArea`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import StoryArea
from typing import Callable


class ExampleStoryArea(StoryArea):
    """Custom handler for StoryArea events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_story_area"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the StoryArea event"""
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
    """Processes the StoryArea event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `position` (Union[St, yAreaPosition]): Position of the area
- `type` (Union[St, yAreaType]): Type of the area
