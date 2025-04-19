# Poll Handler

Telegram Bot API Poll type

## Usage

To create a Poll handler, you need to:

1. Create a class inheriting from `Poll`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import Poll
from typing import Callable


class ExamplePoll(Poll):
    """Custom handler for Poll events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_poll"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the Poll event"""
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
    """Processes the Poll event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `id` (str): Unique poll identifier
- `question` (str): Poll question, 1-300 characters
- `question_entities` (List[MessageEntity]): Optional. Special entities that appear in the question. Currently, only custom emoji entities are allowed in poll questions
- `options` (List[PollOption]): List of poll options
- `total_voter_count` (int): Total number of users that voted in the poll
- `is_closed` (bool): True, if the poll is closed
- `is_anonymous` (bool): True, if the poll is anonymous
- `type` (str): Poll type, currently can be "regular" or "quiz"
- `allows_multiple_answers` (bool): True, if the poll allows multiple answers
- `correct_option_id` (int): Optional. 0-based identifier of the correct answer option. Available only for polls in the quiz mode, which are closed, or was sent (not forwarded) by the bot or to the private chat with the bot.
- `explanation` (str): Optional. Text that is shown when a user chooses an incorrect answer or taps on the lamp icon in a quiz-style poll, 0-200 characters
- `explanation_entities` (List[MessageEntity]): Optional. Special entities like usernames, URLs, bot commands, etc. that appear in the explanation
- `open_period` (int): Optional. Amount of time in seconds the poll will be active after creation
- `close_date` (int): Optional. Point in time (Unix timestamp) when the poll will be automatically closed
