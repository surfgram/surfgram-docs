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
