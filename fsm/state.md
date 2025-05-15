# State

## Package
```python
from surfgram import fsm
```

## Class Description
The `State` class encapsulates a discrete application state with mutable attributes, providing namespaced storage for state-specific data.

## Fields

| Field | Type | Default | Description |
|-------|------|---------|-------------|
| `attributes` | Dict[str, Any] | `field(default_factory=dict)` | Namespaced storage for state variables |
| `name` | str | `""` | Auto-populated by `StatesMeta` metaclass |

## Public Methods

### Attribute Management
```python
def set_attribute(self, name: str, value: Any) -> None
```

#### Description
Stores a named value in the state's attribute store.

#### Parameters
| Parameter | Type | Description |
|-----------|------|-------------|
| `name` | str | Attribute key |
| `value` | Any | Serializable value to store |

#### Persistence
- Attributes persist for the lifetime of the state
- Survives handler re-entrancy
- Shared across all handlers executing in this state

---

```python
def get_attribute(self, name: str, default: Any = None) -> Any
```

#### Description
Retrieves a stored attribute or default value.

#### Returns
| Type | Description |
|------|-------------|
| `Any` | Stored value or default if not found |
=======
Data class representing a single FSM state with attribute storage capabilities.

## Attributes
- `attributes: Dict[str, Any]`: Dictionary storing all state-related data

## Methods

### `set_attribute(name: str, value: Any) -> None`
Store a named value in the state.

### `get_attribute(name: str, default: Any = None) -> Any`
Retrieve a stored value by name. Returns `default` if name doesn't exist.

## Usage Example

```python
from surfgram import fsm

# Create state instance
state = fsm.State()

# Store data
state.set_attribute('user_id', 123)
state.set_attribute('progress', {'step': 2})

# Retrieve data
user_id = state.get_attribute('user_id')
step = state.get_attribute('progress')['step']
missing = state.get_attribute('non_existent', 'default_value')
```
