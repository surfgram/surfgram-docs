# State

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