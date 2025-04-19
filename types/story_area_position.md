# StoryAreaPosition Handler

Telegram Bot API StoryAreaPosition type

## Usage

To create a StoryAreaPosition handler, you need to:

1. Create a class inheriting from `StoryAreaPosition`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import StoryAreaPosition
from typing import Callable


class ExampleStoryAreaPosition(StoryAreaPosition):
    """Custom handler for StoryAreaPosition events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_story_area_position"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the StoryAreaPosition event"""
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
    """Processes the StoryAreaPosition event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `x_percentage` (float): The abscissa of the area's center, as a percentage of the media width
- `y_percentage` (float): The ordinate of the area's center, as a percentage of the media height
- `width_percentage` (float): The width of the area's rectangle, as a percentage of the media width
- `height_percentage` (float): The height of the area's rectangle, as a percentage of the media height
- `rotation_angle` (float): The clockwise rotation angle of the rectangle, in degrees; 0-360
- `corner_radius_percentage` (float): The radius of the rectangle corner rounding, as a percentage of the media width
