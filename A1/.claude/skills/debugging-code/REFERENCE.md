# Code Debugging Skill Reference

## Error Types and Patterns

### 1. Syntax Errors
- **Pattern:** "SyntaxError", "Unexpected token", "Missing '}'"
- **Language Agnostic:** Common to all programming languages
- **Solution Patterns:**
  - Match opening/closing brackets, parentheses, quotes
  - Check proper indentation and formatting
  - Verify semicolons, commas, and other separators

### 2. Reference Errors
- **Pattern:** "Cannot read property", "ReferenceError", "is not defined"
- **Common in:** JavaScript, Python, Java
- **Solution Patterns:**
  - Check variable declarations before use
  - Verify scope (local vs global variables)
  - Ensure proper imports and includes

### 3. Type Errors
- **Pattern:** "TypeError", "Type mismatch", "Cannot convert"
- **Common in:** Dynamically typed languages (JavaScript, Python)
- **Solution Patterns:**
  - Add type checking
  - Convert types explicitly
  - Use type annotations where available

### 4. Null/Undefined Errors
- **Pattern:** "NullPointerException", "Cannot read property of null/undefined"
- **Common in:** Java, JavaScript, C#
- **Solution Patterns:**
  - Add null checks
  - Use optional chaining (?.)
  - Provide default values

### 5. Logic Errors
- **Pattern:** Incorrect output, infinite loops, unexpected behavior
- **Solution Patterns:**
  - Add debug logging
  - Use unit tests
  - Step through code with debugger

## Debugging Commands

### Python Debugging
```python
# Add debug prints
print(f"Variable value: {variable}")
print(f"Type: {type(variable)}")

# Use try-except for specific errors
try:
    # code that might fail
    result = 10 / x
except ZeroDivisionError:
    print("Cannot divide by zero")
    result = 0
```

### JavaScript Debugging
```javascript
// Console debugging
console.log('Variable:', variable);
console.log('Type:', typeof variable);

// Check if variable exists
if (typeof variable !== 'undefined') {
    // safe to use
}

// Optional chaining
const result = obj?.prop?.method?.();
```

### Java Debugging
```java
// Null checks
if (variable != null) {
    // safe to use
}

// Try-catch blocks
try {
    // code that might throw exception
} catch (NullPointerException e) {
    System.out.println("Null pointer caught");
}
```

## Testing Strategies

### 1. Unit Testing
- Test individual functions/methods in isolation
- Verify input/output pairs
- Test edge cases (null, empty, extreme values)

### 2. Integration Testing
- Test how components work together
- Verify API endpoints and database connections
- Test error handling across components

### 3. Debugging Techniques
- **Print Debugging:** Add temporary print statements
- **Step Debugging:** Use debugger tools to step through code
- **Binary Search:** Comment out half the code to isolate issues
- **Rubber Duck Debugging:** Explain code to an inanimate object

## Performance Considerations

### Avoid Common Performance Issues
- **Infinite Loops:** Check loop conditions carefully
- **Memory Leaks:** Close resources, clean up references
- **Slow Operations:** Profile code, optimize algorithms
- **Blocking Operations:** Use async/await, threading where appropriate

## Code Quality Best Practices

### Preventative Measures
1. **Use Linters:** ESLint, Pylint, SonarQube
2. **Write Tests:** Unit tests, integration tests
3. **Code Reviews:** Peer review catch common issues
4. **Documentation:** Comment complex logic
5. **Version Control:** Track changes, revert if needed

### Error Handling Patterns
```javascript
// JavaScript - Error handling
try {
    // risky operation
} catch (error) {
    console.error('Error:', error.message);
    // fallback or recovery
} finally {
    // cleanup
}

// Python - Error handling
try:
    # risky operation
except ValueError as e:
    print(f"Value error: {e}")
except Exception as e:
    print(f"Unexpected error: {e}")
else:
    # success case
finally:
    # cleanup
```

## Debug Tools by Language

### Python
- **Debugger:** pdb, ipdb
- **Profiler:** cProfile, line_profiler
- **Linter:** pylint, flake8
- **Formatter:** black, autopep8

### JavaScript
- **Debugger:** Chrome DevTools, VS Code Debugger
- **Linter:** ESLint
- **Formatter:** Prettier
- **Testing:** Jest, Mocha

### Java
- **Debugger:** IntelliJ IDEA, Eclipse Debugger
- **Profiler:** VisualVM, JProfiler
- **Linter:** Checkstyle, PMD
- **Testing:** JUnit, TestNG

## Common Anti-Patterns to Avoid

### 1. Silent Failures
```javascript
// Bad - errors are ignored
try {
    riskyOperation();
} catch (e) {
    // do nothing - error is hidden
}

// Good - handle or log errors
try {
    riskyOperation();
} catch (e) {
    console.error('Operation failed:', e);
    // handle appropriately
}
```

### 2. Magic Numbers and Strings
```javascript
// Bad - unclear what these values mean
if (status === 1) {
    // do something
}

// Good - use constants
const STATUS_ACTIVE = 1;
if (status === STATUS_ACTIVE) {
    // do something
}
```

### 3. Deeply Nested Conditions
```javascript
// Bad - hard to read
if (condition1) {
    if (condition2) {
        if (condition3) {
            // action
        }
    }
}

// Good - flatten or early return
if (!condition1 || !condition2 || !condition3) {
    return;
}
// action
```

This reference provides comprehensive debugging patterns and solutions that complement the main skill instructions.