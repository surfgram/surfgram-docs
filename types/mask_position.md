# MaskPosition Handler

Telegram Bot API MaskPosition type

## Usage

To create a MaskPosition handler, you need to:

1. Create a class inheriting from `MaskPosition`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import MaskPosition
from typing import Callable


class ExampleMaskPosition(MaskPosition):
    """Custom handler for MaskPosition events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_mask_position"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the MaskPosition event"""
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
    """Processes the MaskPosition event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `point` (str): The part of the face relative to which the mask should be placed. One of "forehead", "eyes", "mouth", or "chin".
- `x_shift` (float): Shift by X-axis measured in widths of the mask scaled to the face size, from left to right. For example, choosing -1.0 will place mask just to the left of the default mask position.
- `y_shift` (float): Shift by Y-axis measured in heights of the mask scaled to the face size, from top to bottom. For example, 1.0 will place the mask just below the default mask position.
- `scale` (float): Mask scaling coefficient. For example, 2.0 means double size.
