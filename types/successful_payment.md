# SuccessfulPayment

Telegram Bot API SuccessfulPayment type

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
from surfgram.types import SuccessfulPayment

class MySuccessfulPaymentHandler(SuccessfulPayment):    
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
| `currency` | `str` | Three-letter ISO 4217 currency code, or "XTR" for payments in Telegram Stars |
| `total_amount` | `int` | Total price in the smallest units of the currency (integer, not float/double). For example, for a price of US$ 1.45 pass amount = 145. See the exp parameter in currencies.json, it shows the number of digits past the decimal point for each currency (2 for the majority of currencies). |
| `invoice_payload` | `str` | Bot-specified invoice payload |
| `subscription_expiration_date` | `int` | Optional. Expiration date of the subscription, in Unix time; for recurring payments only |
| `is_recurring` | `bool` | Optional. True, if the payment is a recurring payment for a subscription |
| `is_first_recurring` | `bool` | Optional. True, if the payment is the first payment for a subscription |
| `shipping_option_id` | `str` | Optional. Identifier of the shipping option chosen by the user |
| `order_info` | `OrderInfo` | Optional. Order information provided by the user |
| `telegram_payment_charge_id` | `str` | Telegram payment identifier |
| `provider_payment_charge_id` | `str` | Provider payment identifier |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
