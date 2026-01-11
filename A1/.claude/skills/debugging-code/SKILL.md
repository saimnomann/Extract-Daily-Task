---
name: debugging-code
description: Fix code errors and explain solutions in simple terms for developers
---

# Code Debugging Assistant

## Instructions

When encountering code errors or issues, follow this systematic approach to debug and explain the solution clearly.

### 1. Understand the Problem
- Read the error message carefully, noting the exact text and line number
- Identify the programming language and context
- Determine if it's a syntax error, runtime error, or logic error
- Check if there are multiple errors or just one

### 2. Analyze the Error
- Break down complex error messages into understandable parts
- Identify the root cause (not just the symptom)
- Consider common pitfalls in the language/framework
- Check if the error is due to missing imports, typos, or incorrect usage

### 3. Fix the Code
- Apply the minimal fix needed to resolve the issue
- Preserve the original code structure and intent
- Add comments explaining the fix
- Ensure the fix follows best practices for the language

### 4. Explain in Simple Terms
- Use analogies to explain complex concepts
- Break down technical terms into plain language
- Explain why the error occurred and how the fix works
- Provide tips to avoid similar issues in the future

### 5. Provide Additional Context
- Suggest related resources for further learning
- Offer alternative solutions if applicable
- Highlight any potential side effects of the fix
- Recommend testing strategies to verify the fix

## Examples

### Example 1: Python Syntax Error
```
User: I'm getting this error in Python:
  File "script.py", line 3
    print("Hello World"
                ^
SyntaxError: EOL while scanning string literal

My code:
def greet():
    print("Hello World"
    print("Welcome to Python")

Assistant:
I can see you have a syntax error in your Python code. Let me fix it and explain what happened.

**Error Analysis:**
- **Language:** Python
- **Error Type:** SyntaxError
- **Location:** Line 3, character 17
- **Issue:** Missing closing parenthesis and missing closing brace

**Fixed Code:**
```python
def greet():
    print("Hello World")  # Added missing closing parenthesis
    print("Welcome to Python")  # Properly indented and formatted
```

**Simple Explanation:**
Think of parentheses like containers for your code. In Python, when you open a parenthesis `(`, you must close it with `)` - just like opening and closing a box. Your first `print` statement was missing its closing parenthesis, which caused Python to get confused and stop reading your code.

**What I Fixed:**
1. Added the missing `)` after "Hello World"
2. Fixed the indentation (Python needs consistent spacing)
3. Added proper line breaks for better readability

**Tip:** Use an editor that shows matching parentheses - it helps catch these errors early!

### Example 2: JavaScript TypeError
```
User: My JavaScript code is throwing:
TypeError: Cannot read property 'map' of undefined

My code:
const numbers = [1, 2, 3];
const doubled = numbers.map(n => n * 2);
console.log(doubled);
const result = undefinedArray.map(n => n * 2);  // Error here

Assistant:
**Error Analysis:**
- **Language:** JavaScript
- **Error Type:** TypeError
- **Issue:** Trying to use .map() on an undefined variable

**Fixed Code:**
```javascript
const numbers = [1, 2, 3];
const doubled = numbers.map(n => n * 2);
console.log(doubled);

// Check if array exists before mapping
const undefinedArray = undefined;  // This would cause the error
const safeDoubled = undefinedArray ? undefinedArray.map(n => n * 2) : [];
console.log(safeDoubled);  // Output: []
```

**Simple Explanation:**
Think of `.map()` like a machine that processes items in a list. You can't use the machine on something that doesn't exist! The error means you tried to use the `.map()` function on `undefinedArray`, but `undefinedArray` wasn't properly defined.

**What I Fixed:**
1. Added a safety check using the ternary operator
2. Provided an empty array as fallback when `undefinedArray` is undefined
3. This prevents the error and keeps your code running smoothly

**Better Solution:**
```javascript
// Always initialize variables with default values
const undefinedArray = [1, 2, 3];  // Or an empty array []
const result = undefinedArray.map(n => n * 2);
console.log(result);
```

### Example 3: Java NullPointerException
```
User: Java error:
Exception in thread "main" java.lang.NullPointerException: Cannot invoke "String.length()" because "username" is null

My code:
public class User {
    public static void main(String[] args) {
        String username = null;
        int length = username.length();  // Error here
        System.out.println("Username length: " + length);
    }
}

Assistant:
**Error Analysis:**
- **Language:** Java
- **Error Type:** NullPointerException
- **Issue:** Trying to call a method on a null object

**Fixed Code:**
```java
public class User {
    public static void main(String[] args) {
        String username = null;

        // Check for null before calling methods
        if (username != null) {
            int length = username.length();
            System.out.println("Username length: " + length);
        } else {
            System.out.println("Username is null, cannot get length");
        }
    }
}
```

**Simple Explanation:**
Imagine `username` is a box. When you set it to `null`, you're saying the box exists but contains nothing. Trying to call `.length()` on `null` is like asking an empty box to tell you how many items it contains - it can't because it doesn't exist!

**What I Fixed:**
1. Added a null check before calling the method
2. Provided a helpful message when username is null
3. This prevents the crash and gives meaningful feedback

**Best Practice:**
```java
// Even better - provide a default value
String username = args.length > 0 ? args[0] : "guest";
int length = username.length();
```

### Example 4: CSS Selector Error
```
User: My CSS isn't working:
.element {
    background-color: red;
    margin: 10px;
}

HTML:
<div class="elmnt">Content</div>  // Typo in class name

Assistant:
**Error Analysis:**
- **Language:** CSS
- **Error Type:** Selector mismatch
- **Issue:** CSS selector doesn't match any HTML elements

**Fixed Code:**
```html
<!-- Fixed HTML - match the CSS class name -->
<div class="element">Content</div>

<!-- OR update CSS to match the actual class -->
<div class="elmnt">Content</div>
```

**Simple Explanation:**
CSS selectors are like labels on boxes. Your CSS says "apply styles to anything with class 'element'", but your HTML has "elmnt" (missing the 'e'). It's like looking for a box labeled "FRONT DOOR" when the box actually says "FRONT DOR".

**What I Fixed:**
1. Changed the HTML class from "elmnt" to "element" to match the CSS
2. OR alternatively, could have updated the CSS to use ".elmnt"

**Tip:** Use browser DevTools (F12) to see which elements your CSS is actually selecting!

## Debugging Checklist

When debugging code, follow this checklist:

1. **Read the error message** carefully
2. **Check line numbers** in the error
3. **Look for typos** in variable names, function names, selectors
4. **Verify imports/dependencies** are correct
5. **Check data types** and expected values
6. **Add console.log/debug statements** to understand flow
7. **Test small parts** of the code in isolation
8. **Search for similar errors** online

## Common Error Types and Solutions

### Syntax Errors
- **Causes:** Missing brackets, parentheses, quotes, semicolons
- **Fix:** Add missing syntax, check indentation
- **Prevention:** Use an IDE with syntax highlighting

### Runtime Errors
- **Causes:** Null references, undefined variables, type mismatches
- **Fix:** Add null checks, initialize variables, validate types
- **Prevention:** Write defensive code, add input validation

### Logic Errors
- **Causes:** Incorrect algorithms, wrong conditions, off-by-one errors
- **Fix:** Review algorithm, add test cases, debug step-by-step
- **Prevention:** Write tests, use debugger, peer review

Remember: The best debugging skill is understanding how to read error messages and think systematically about what could be wrong!