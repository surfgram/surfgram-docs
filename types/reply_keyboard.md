# ReplyKeyboard

Telegram Bot API reply keyboard markup generator.

## Required Implementation
Subclasses **must** implement:

```python
@property
def __keyboard__(self) -> List[List["ReplyKeyboardButton"]]:
    """Returns 2D list of ReplyKeyboardButton objects"""
```

## Usage Example

```python
class MyKeyboard(ReplyKeyboard):
    @property
    def __keyboard__(self):
        return [
            [ReplyKeyboardButton(text="Option 1", callback_data="opt1")],
            [ReplyKeyboardButton(text="Option 2", callback_data="opt2")]
        ]

# Automatically converts to Telegram markup
keyboard = MyKeyboard()  
# {'keyboard': [[{'text':'Option 1',...}],...]}
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