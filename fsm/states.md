# States

## Package
```python
from surfgram import fsm
```

## Class Description
The `States` class provides hierarchical state management with configurable storage backends, enabling state persistence across chat sessions.

## Storage Configuration
Configure storage via class attribute:
```python
class MyStates(fsm.States):
    __provider__ = RedisStorage
```

Default: `InMemoryStorage` (volatile memory storage)

## Public Interface

### State Management
```python
@classmethod
def turn(cls: Type[T], state: State, chat_id: int) -> None
```

#### Description
Transitions a chat to the specified state, preserving all state attributes.

#### Parameters
| Parameter | Type | Description |
|-----------|------|-------------|
| `state` | State | Target state object |
| `chat_id` | int | Target chat identifier |

#### Example
```python
await MyStates.turn(MyStates.MAIN_MENU, update.chat.id)
```

---

```python
@classmethod
def get_current(cls: Type[T], chat_id: int) -> Optional[State]
```

#### Description
Retrieves the current state with all persisted attributes.

#### Returns
| Type | Description |
|------|-------------|
| `Optional[State]` | Current state or None if no state set |

---

```python
@classmethod
def reset(cls: Type[T], chat_id: int) -> None
```

#### Description
Clears all state information for the specified chat.

---

### State Inspection
```python
@classmethod
def is_current(cls: Type[T], state: State, chat_id: int) -> bool
```

#### Description
Verifies whether a chat is in the specified state.

#### Aliases
- `received()` provides identical functionality

---

### Attribute Management
```python
@classmethod
def set_attribute(cls: Type[T], chat_id: int, name: str, value: Any) -> None
```

#### Description
Persists a state attribute across handler executions.

#### Storage Notes
Attributes are stored with the current state and persist until:
- State change
- Explicit removal
- State reset

---

```python
@classmethod
def get_attribute(cls: Type[T], chat_id: int, name: str, default: Any = None) -> Any
```

#### Description
Retrieves a persisted state attribute.
=======
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
