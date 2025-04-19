# TransactionPartnerUser Handler

Telegram Bot API TransactionPartnerUser type

## Usage

To create a TransactionPartnerUser handler, you need to:

1. Create a class inheriting from `TransactionPartnerUser`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import TransactionPartnerUser
from typing import Callable


class ExampleTransactionPartnerUser(TransactionPartnerUser):
    """Custom handler for TransactionPartnerUser events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_transaction_partner_user"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the TransactionPartnerUser event"""
        # Your implementation here
        pass
```

## Required Properties

### `__names__`
- **Type**: `List[str]`
- **Description**: List of trigger names that will activate this handler
- **Example**: `return ["start", "begin"]`

### `__callback__`
- **Type**: `Callable`
- **Description**: Returns the async function that will process the event
- **Signature**: `async def callback(update, bot) -> None`

## Handler Method

Your handler method should have the following signature:

```python
async def handle(self, update, bot):
    """Processes the TransactionPartnerUser event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Type of the transaction partner, always "user"
- `transaction_type` (str): Type of the transaction, currently one of "invoice_payment" for payments via invoices, "paid_media_payment" for payments for paid media, "gift_purchase" for gifts sent by the bot, "premium_purchase" for Telegram Premium subscriptions gifted by the bot, "business_account_transfer" for direct transfers from managed business accounts
- `user` (User): Information about the user
- `affiliate` (AffiliateInfo): Optional. Information about the affiliate that received a commission via this transaction. Can be available only for "invoice_payment" and "paid_media_payment" transactions.
- `invoice_payload` (str): Optional. Bot-specified invoice payload. Can be available only for "invoice_payment" transactions.
- `subscription_period` (int): Optional. The duration of the paid subscription. Can be available only for "invoice_payment" transactions.
- `paid_media` (List[PaidMedia]): Optional. Information about the paid media bought by the user; for "paid_media_payment" transactions only
- `paid_media_payload` (str): Optional. Bot-specified paid media payload. Can be available only for "paid_media_payment" transactions.
- `gift` (Gift): Optional. The gift sent to the user by the bot; for "gift_purchase" transactions only
- `premium_subscription_duration` (int): Optional. Number of months the gifted Telegram Premium subscription will be active for; for "premium_purchase" transactions only
