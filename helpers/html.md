# HTML

Static class for generating HTML-formatted text for Telegram messages (parse_mode='HTML')

## Features
- Provides clean syntax for all Telegram-supported HTML tags
- Type-safe formatting methods
- Composable formatting (can nest formatting calls)

## Available Formatting Methods

### Text Styles
```python
HTML.bold("text")        # <b>text</b>
HTML.italic("text")      # <i>text</i> 
HTML.underline("text")   # <u>text</u>
HTML.strikethrough("text") # <s>text</s>
HTML.spoiler("text")     # <tg-spoiler>text</tg-spoiler>
```

### Code Formatting  
```python
HTML.inline_code("code") # <code>code</code>
HTML.code_block("code")  # <pre><code>code</code></pre>
HTML.preformatted("text") # <pre>text</pre>
```

### Links & Mentions
```python
HTML.link("text", "https://example.com") # <a href="...">text</a>
HTML.mention("John", 12345) # <a href="tg://user?id=12345">John</a> 
```

## Usage Example

```python
from surfgram.formatting import HTML

message = f"""
{HTML.bold("Important Update")}
{HTML.italic("Please read carefully")}

{HTML.link("Documentation", "https://docs.example.com")}

Code example:
{HTML.code_block("def hello():\n    print('Hello!')", "python")}
"""

await bot.send_message(
    chat_id=chat_id,
    text=message,
    parse_mode="HTML"
)
```

## Notes
- Always set `parse_mode="HTML"` when sending
- Tags must be properly nested and closed
- Supports all Telegram Bot API HTML formatting options
- Escaping is handled automatically by the library
