# States

Core class for Finite State Machine (FSM) management in Surfgram framework. Tracks and manipulates states per chat ID.

## Class Methods

### `turn(state: State, chat_id: int) -> None`
Set current state for a chat.

### `get_current(chat_id: int) -> Optional[State]`
Get current state for a chat. Returns `None` if no state set.

### `reset(chat_id: int) -> None`
Clear current state for a chat.

### `is_current(state: State, chat_id: int) -> bool`
Check if specified state is current for a chat.

### `received(state: State, chat_id: int) -> bool`
Alias for `is_current()`.

### `set_attribute(chat_id: int, name: str, value: Any) -> None`
Set attribute in current state's storage.

### `get_attribute(chat_id: int, name: str, default: Any = None) -> Any`
Get attribute from current state's storage. Returns `default` if not found.

## Storage
- `_states_storage: Dict[int, State]`: Internal dictionary mapping chat IDs to their states

## Usage Example

```python
from surfgram import fsm

# Define states
class MyStates(fsm.States):
    MAIN_MENU = fsm.State()
    AWAITING_INPUT = fsm.State()

# Set state
MyStates.turn(MyStates.MAIN_MENU, chat_id=123)

# Check state
if MyStates.is_current(MyStates.MAIN_MENU, chat_id=123):
    print("User is in main menu")

# Store data
MyStates.set_attribute(123, 'user_data', {'name': 'John'})

# Retrieve data
data = MyStates.get_attribute(123, 'user_data')
```