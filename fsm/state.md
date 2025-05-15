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
