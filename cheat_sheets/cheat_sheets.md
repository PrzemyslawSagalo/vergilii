# Cheat Sheets

## Python

### Naming convention for functions and variables
| C++ Access Specifier | Python Convention          | Description                                                                                  |
|----------------------|---------------------------|-----------------------------------------------------------------------------------------------|
| Public               | (No specific convention)  | Members are accessible from outside the class.                                                |
| Private              | Double underscore `__foo` | Members are not directly accessible from outside the class. Name mangling changes the name to include the class name, preventing accidental access. |
| Protected            | Single underscore `_foo`  | By convention, these are for internal use. They can still be accessed, reflecting Python's flexible approach. |

**Name Mangling:**
When a child class and its parent class both have attributes named with double underscores (`__private_var`), Python treats them as separate attributes. This is because Python changes the name of these attributes to include the class name (`_Parent__private_var` for the parent and `_Child__private_var` for the child). This ensures they don't interfere with each other, keeping the parents' attributes separate from the child's.
