# InlineKeyboard

Telegram Bot API inline keyboard markup generator.


## Core Features
- Generates Telegram-compatible inline keyboard markups
- Auto-converts to dictionary format when instantiated
- Supports additional markup parameters via kwargs

## Required Implementation
Subclasses **must** implement:

```python
@property
def __keyboard__(self) -> List[List["InlineKeyboardButton"]]:
    """Returns 2D list of InlineKeyboardButton objects"""
```

## Usage Example

```python
class MyKeyboard(InlineKeyboard):
    @property
    def __keyboard__(self):
        return [
            [InlineKeyboardButton(text="Option 1", callback_data="opt1")],
            [InlineKeyboardButton(text="Option 2", callback_data="opt2")]
        ]

# Automatically converts to Telegram markup
keyboard = MyKeyboard()  
# {'inline_keyboard': [[{'text':'Option 1',...}],...]}
```

## Key Methods

### `to_markup(**kwargs) -> Dict[str, Any]`
Converts keyboard to Telegram API format:
- Merges any additional parameters (e.g., `resize_keyboard`)
- Returns ready-to-use markup dictionary

## Behavior
- Instances automatically convert to markup dictionaries
- String representations show the generated markup
- Designed for direct use in Telegram API calls