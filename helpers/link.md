# Link

Telegram Bot API documentation link builder (internal use)

## Internal Use Only

Used exclusively for building `BotError` documentation links. Do not use directly.

## Example

```python
# Inside BotError implementation:
doc_link = Link("/api#sendmessage")
print(doc_link)  # "https://core.telegram.org/bots/api#sendmessage"
```

> Note: This is an internal utility class. Use `BotError` for proper error handling.