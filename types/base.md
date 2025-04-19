# TypesFactory

Core type registration and resolution system

## Usage

### 1. Register Types
```python
class Message(metaclass=FactoryMeta):
    __type_name__ = "message"
```

### 2. Get Handler
```python
handler_class = TypesFactory.get_instance(update)
```

## Key Features

- Automatic type registration via `FactoryMeta`
- Deep search in update structures
- Supports both key and value matching
- Centralized type management

## Methods

### `register_type(type_cls)`
Registers class if it has `__type_name__`

### `get_instance(update)`
Finds matching handler for update:
1. Checks for `__type_name__` as key
2. Checks for `__type_name__` as value
3. Returns None if no match

## Internal Utilities
- `_key_exists()`: Recursive key search
- `_value_exists()`: Recursive value search