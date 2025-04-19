# InlineKeyboardButton 

Telegram Bot API inline keyboard button representation.

## Purpose
Represents a button in Telegram's inline keyboard markup.

## Usage

### Basic Initialization
```python
button = InlineKeyboardButton(
    text="Click me"
)
```

### Dictionary Conversion
```python
button_data = button.to_dict()  
# {'text': 'Click me'}
```
