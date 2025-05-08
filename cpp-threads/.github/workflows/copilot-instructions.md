# Copilot Code Generation Instructions

## General Guidelines
- Use camelCase for variable and function names.
- Use PascalCase for class names.
- Use double quotes for strings.
- Ensure all functions have Doxygen comments.
- Ensure consistent indentation using 2 spaces.
- Use 'm_' as a prefix for private and protected member variables.
- Separate implementation and design by using header (`.h` or `.hpp`) and source (`.cpp`) files.
- Favor composition over inheritance where possible.

## Specific Instructions
- Use `const` for variables that do not change.
- Use `auto` for type inference where appropriate.
- Prefer lambda functions for anonymous functions.
- Use `std::stringstream` for string concatenation. 
- Ensure all functions handle errors using exceptions. 
- Verify that all included headers are used.
- Check for proper error handling in all functions.
- Ensure all loops have proper termination conditions.
- Use descriptive names for variables and functions.
- Avoid deeply nested code; refactor into smaller functions if necessary.
- Ensure all promises are properly awaited using `std::future`. [Reference](https://en.cppreference.com/w/cpp/thread/future)
- Verify that all dependencies are listed in `CMakeLists.txt`.
- Check for any potential performance issues.
- Ensure all abstract base classes have a virtual destructor. 

## Testing Guidelines
- Use DocTest for all tests. [Reference](https://github.com/onqtam/doctest)
- Ensure all tests are self-contained and do not rely on external state.
- Write tests for all public functions and classes.
- Ensure tests cover both typical and edge cases.
- Use descriptive names for test cases and functions.

### Example Test Snippet

```cpp
#define DOCTEST_CONFIG_IMPLEMENT_WITH_MAIN
#include "doctest.h"

TEST_CASE("Basic Arithmetic") {
  CHECK(2 * 3 == 6);
  CHECK(10 / 2 == 5);
}

TEST_CASE("String Concatenation") {
  CHECK(std::string("Test") + "ing" == "Testing");
}
```

