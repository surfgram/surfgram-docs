# Markdown

Static class for generating MarkdownV2-formatted text for Telegram messages (parse_mode='MarkdownV2')

## Features
- Provides clean syntax for all Telegram-supported Markdown formatting
- Type-safe formatting methods
- Composable formatting (can nest formatting calls)
- Supports both Markdown and MarkdownV2 parse modes

## Available Formatting Methods

### Text Styles
```python
Markdown.bold("text")        # **text**
Markdown.italic("text")      # __text__
Markdown.strikethrough("text") # ~~text~~
Markdown.spoiler("text")     # ||text||
```

### Code Formatting
```python
Markdown.inline_code("code") # `code`
Markdown.code_block("code")  # ```\ncode\n```
Markdown.code_block("code", "python")  # ```python\ncode\n```
```

### Links & Mentions
```python
Markdown.link("text", "https://example.com") # [text](https://example.com)
Markdown.mention("John", 12345) # [John](tg://user?id=12345)
```

## Usage Example

```python
from surfgram.formatting import Markdown

message = f"""
{Markdown.bold("Important Notice")}
{Markdown.italic("Please acknowledge")}

{Markdown.link("View Docs", "https://docs.example.com")}

Example code:
{Markdown.code_block("def hello():\n    print('Hello!')", "python")}
"""

await bot.send_message(
    chat_id=chat_id,
    text=message,
    parse_mode="MarkdownV2"  # or "Markdown"
)
```

## Important Notes
1. For MarkdownV2 mode (recommended):
   - You must escape these characters: `_*[]()~`>#+-=|{}.!`
   - Use `MarkdownV2` class for automatic escaping

2. For legacy Markdown mode:
   - Limited formatting support
   - Doesn't support underline or nested formatting

3. Always specify the correct parse_mode when sending:
   ```python
   parse_mode="MarkdownV2"  # recommended
   parse_mode="Markdown"    # legacy
   ```

> Tip: Use MarkdownV2 for best results and most consistent rendering across Telegram clients.