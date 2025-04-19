# ReplyKeyboardButton

Telegram Bot API reply keyboard button representation.

## Purpose
Represents a button in Telegram's reply keyboard markup.

## Usage

### Basic Initialization
```python
button = ReplyKeyboardButton(
    text="Click me",
    request_contact=True
)
```

### Dictionary Conversion
```python
button_data = button.to_dict()  
# {'text': 'Click me', 'request_contact': True}
```
