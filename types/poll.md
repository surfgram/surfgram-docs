# Poll

Telegram Bot API Poll type

## Overview

| Property        | Type               | Required | Default | Description                              |
|-----------------|--------------------|----------|---------|------------------------------------------|
| `__is_active__` | `bool`             | No       | `True`  | Global handler switch                   |
| `__names__`     | `List[str]`        | No       | `[]`    | Trigger filter (empty = all)            |
| `__callback__`  | `Callable`         | **Yes**  | -       | Async handler function                  |

## Implementation Guide

### Basic Template

```python
from typing import List, Callable
from surfgram.types import Poll

class MyPollHandler(Poll):    
    @property
    def __is_active__(self) -> bool:
        return True  # Set False to disable
        
    @property
    def __names__(self) -> List[str]:
        return []  # ['specific_trigger'] for filtered handling
        
    @property
    def __callback__(self) -> Callable:
        return self.process_event
        
    async def process_event(self, update: dict, bot) -> None:
        """Main handler logic"""
        # Implement your processing here
```

### Field Reference

The update object contains these fields:

| Field          | Type              | Description                     |
|----------------|-------------------|---------------------------------|
| `id` | `str` | Unique poll identifier |
| `question` | `str` | Poll question, 1-300 characters |
| `question_entities` | `List[MessageEntity]` | Optional. Special entities that appear in the question. Currently, only custom emoji entities are allowed in poll questions |
| `options` | `List[PollOption]` | List of poll options |
| `total_voter_count` | `int` | Total number of users that voted in the poll |
| `is_closed` | `bool` | True, if the poll is closed |
| `is_anonymous` | `bool` | True, if the poll is anonymous |
| `type` | `str` | Poll type, currently can be "regular" or "quiz" |
| `allows_multiple_answers` | `bool` | True, if the poll allows multiple answers |
| `correct_option_id` | `int` | Optional. 0-based identifier of the correct answer option. Available only for polls in the quiz mode, which are closed, or was sent (not forwarded) by the bot or to the private chat with the bot. |
| `explanation` | `str` | Optional. Text that is shown when a user chooses an incorrect answer or taps on the lamp icon in a quiz-style poll, 0-200 characters |
| `explanation_entities` | `List[MessageEntity]` | Optional. Special entities like usernames, URLs, bot commands, etc. that appear in the explanation |
| `open_period` | `int` | Optional. Amount of time in seconds the poll will be active after creation |
| `close_date` | `int` | Optional. Point in time (Unix timestamp) when the poll will be automatically closed |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
