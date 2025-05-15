# StarTransaction

Telegram Bot API StarTransaction type

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
from surfgram.types import StarTransaction

class MyStarTransactionHandler(StarTransaction):    
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
| `id` | `str` | Unique identifier of the transaction. Coincides with the identifier of the original transaction for refund transactions. Coincides with SuccessfulPayment.telegram_payment_charge_id for successful incoming payments from users. |
| `amount` | `int` | Integer amount of Telegram Stars transferred by the transaction |
| `nanostar_amount` | `int` | Optional. The number of 1/1000000000 shares of Telegram Stars transferred by the transaction; from 0 to 999999999 |
| `date` | `int` | Date the transaction was created in Unix time |
| `source` | `TransactionPartner` | Optional. Source of an incoming transaction (e.g., a user purchasing goods or services, Fragment refunding a failed withdrawal). Only for incoming transactions |
| `receiver` | `TransactionPartner` | Optional. Receiver of an outgoing transaction (e.g., a user for a purchase refund, Fragment for a withdrawal). Only for outgoing transactions |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
