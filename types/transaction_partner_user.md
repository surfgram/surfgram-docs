# TransactionPartnerUser

Telegram Bot API TransactionPartnerUser type

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
from surfgram.types import TransactionPartnerUser

class MyTransactionPartnerUserHandler(TransactionPartnerUser):    
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
| `type` | `str` | Type of the transaction partner, always "user" |
| `transaction_type` | `str` | Type of the transaction, currently one of "invoice_payment" for payments via invoices, "paid_media_payment" for payments for paid media, "gift_purchase" for gifts sent by the bot, "premium_purchase" for Telegram Premium subscriptions gifted by the bot, "business_account_transfer" for direct transfers from managed business accounts |
| `user` | `User` | Information about the user |
| `affiliate` | `AffiliateInfo` | Optional. Information about the affiliate that received a commission via this transaction. Can be available only for "invoice_payment" and "paid_media_payment" transactions. |
| `invoice_payload` | `str` | Optional. Bot-specified invoice payload. Can be available only for "invoice_payment" transactions. |
| `subscription_period` | `int` | Optional. The duration of the paid subscription. Can be available only for "invoice_payment" transactions. |
| `paid_media` | `List[PaidMedia]` | Optional. Information about the paid media bought by the user; for "paid_media_payment" transactions only |
| `paid_media_payload` | `str` | Optional. Bot-specified paid media payload. Can be available only for "paid_media_payment" transactions. |
| `gift` | `Gift` | Optional. The gift sent to the user by the bot; for "gift_purchase" transactions only |
| `premium_subscription_duration` | `int` | Optional. Number of months the gifted Telegram Premium subscription will be active for; for "premium_purchase" transactions only |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
