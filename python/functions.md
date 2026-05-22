# Positional vs Keyword Arguments (Performance & Architecture)

In Python (CPython), the way arguments are passed to a function directly impacts memory allocation, CPU throughput, and system architecture.

## 1. Positional-Only Arguments

Arguments are mapped directly to the function's internal variable array based solely on their order (index).

```python
def process(data, config, /):  # '/' enforces positional-only arguments
    pass

process(raw_data, current_config)
```

### Low-Level Characteristics:
* **Performance (Tier 1):** The fastest possible way to invoke a function in Python. The interpreter completely skips name parsing and lookups.
* **Zero Dictionary Allocation:** Values are placed directly into a C-level array of pointers (`PyObject*` in CPython).
* **Use Cases:** Algorithms, data structures, High-Frequency Trading (HFT) systems, mathematical operations (e.g., tail recursion), and internal helper functions (private APIs).

---

## 2. Keyword-Only Arguments

Arguments are passed as explicit key-value pairs, meaning their order in the function call does not matter.

```python
def create_user(*, user_id: int, email: str):  # '*' enforces keyword-only arguments
    pass

create_user(email="dev@example.com", user_id=42)
```

### Low-Level Characteristics:
* **Memory Overhead:** For every single execution, CPython must instantiate a temporary dictionary (`dict`) under the hood, calculate hashes for the string keys (`'user_id'`, `'email'`), and map them to the function parameters.
* **Refactoring Safety:** Changing the order of parameters or adding new optional fields does not break backward compatibility or client contracts.
* **Use Cases:** Business logic, Domain-Driven Design (DDD) services, component constructors, public APIs, and system configurations. *Explicit is better than implicit.*
