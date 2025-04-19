# StoryAreaTypeSuggestedReaction Handler

Telegram Bot API StoryAreaTypeSuggestedReaction type

## Usage

To create a StoryAreaTypeSuggestedReaction handler, you need to:

1. Create a class inheriting from `StoryAreaTypeSuggestedReaction`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import StoryAreaTypeSuggestedReaction
from typing import Callable


class ExampleStoryAreaTypeSuggestedReaction(StoryAreaTypeSuggestedReaction):
    """Custom handler for StoryAreaTypeSuggestedReaction events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_story_area_type_suggested_reaction"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the StoryAreaTypeSuggestedReaction event"""
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
    """Processes the StoryAreaTypeSuggestedReaction event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Type of the area, always "suggested_reaction"
- `reaction_type` (ReactionType): Type of the reaction
- `is_dark` (bool): Optional. Pass True if the reaction area has a dark background
- `is_flipped` (bool): Optional. Pass True if reaction area corner is flipped
