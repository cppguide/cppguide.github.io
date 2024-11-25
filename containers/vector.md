# Introduction to std::vector

The `std::vector` is a sequence container in the C++ Standard Library that encapsulates dynamic size arrays. It is part of the `<vector>` header and provides a way to manage a collection of elements that can grow and shrink in size dynamically. The `std::vector` is one of the most commonly used containers due to its flexibility and ease of use.

## Key Features of std::vector

- **Dynamic Sizing**: Unlike arrays, `std::vector` can change its size dynamically, allowing elements to be added or removed as needed.
- **Contiguous Storage**: Elements in a `std::vector` are stored in contiguous memory locations, which means that they can be accessed using pointer arithmetic and provide cache-friendly access patterns.
- **Efficient Access**: Provides constant time complexity for element access using the subscript operator (`[]`) or the `at()` method.
- **Range-based Operations**: Supports a wide range of operations, including iterators, which allow for easy traversal and manipulation of elements.
- **Automatic Memory Management**: Handles memory allocation and deallocation automatically, reducing the risk of memory leaks and other memory-related issues.

## Additional Information

- **Capacity and Size**: `std::vector` has a `size()` method to get the number of elements currently stored and a `capacity()` method to get the total storage capacity. The capacity is always greater than or equal to the size, and it grows automatically as elements are added.
- **Modifiers**: Includes a variety of methods to modify the contents, such as `push_back()`, `pop_back()`, `insert()`, `erase()`, `clear()`, and `resize()`.
- **Exception Safety**: Provides strong exception safety guarantees. If an exception is thrown during an operation, the `std::vector` remains in a valid state.
- **Allocator Support**: Allows custom memory allocators to be used, providing flexibility in memory management strategies.

## Basic Usage

To use `std::vector`, you need to include the `<vector>` header and create a `std::vector` object. Here is a simple example:

```cpp
#include <vector>
#include <iostream>

int main() {
    std::vector<int> vec;
    vec.push_back(10);
    std::cout << "Vector size: " << vec.size() << std::endl;
    return 0;
}
```
