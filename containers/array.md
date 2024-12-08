# Introduction to std::array

The `std::array` is a fixed-size sequence container in the C++ Standard Library that encapsulates a static array. It is part of the `<array>` header and provides a safer, more convenient alternative to C-style arrays while maintaining the same performance characteristics.

## Example Usage

Before using `std::array`, make sure to include the `<array>` header:

```cpp
#include <array>
```

If you don't want to use `std::` as prefix, you can alias it:

```cpp
using namespace std;
```

NOTE: The following examples will use the alias `array` for `std::array` and will not include the header.

### Creating an array

#### Default constructor

```cpp
array<int, 5> arr;  // Uninitialized array of 5 integers
```

#### Initializer list constructor

```cpp
array<int, 5> arr = {1, 2, 3, 4, 5};
array<int, 5> arr2{1, 2, 3};  // Elements 4 and 5 are zero-initialized
```

#### Copy constructor

```cpp
array<int, 5> arr3(arr);
array<int, 5> arr4 = arr;
```

### Accessing elements

```cpp
array<int, 5> arr = {1, 2, 3, 4, 5};
// no bounds checking
cout << arr[0] << endl; // 1
// with bounds checking, throws an exception if the index is out of bounds
cout << arr.at(0) << endl; // 1

// first element
cout << arr.front() << endl; // 1
// last element
cout << arr.back() << endl; // 5

// get raw pointer to the underlying array
int* data = arr.data();
```

### Iterating over an array

```cpp
array<int, 5> arr = {1, 2, 3, 4, 5};
// range-based for loop with const reference
for (const auto& elem : arr) {
    cout << elem << " ";
}
// using const iterators
for (auto it = arr.cbegin(); it != arr.cend(); ++it) {
    cout << *it << " ";
}
// using reverse const iterators
for (auto it = arr.crbegin(); it != arr.crend(); ++it) {
    cout << *it << " ";
}

// range-based for loop with non-const reference
for (auto& elem : arr) {
    cout << elem << " ";
}
// using non-const iterators
for (auto it = arr.begin(); it != arr.end(); ++it) {
    cout << *it << " ";
}
// using reverse non-const iterators
for (auto it = arr.rbegin(); it != arr.rend(); ++it) {
    cout << *it << " ";
}
```

### Modifying an array

```cpp
array<int, 5> arr = {1, 2, 3, 4, 5};
// modify individual elements
arr[0] = 10;
arr.at(1) = 20;

// fill the entire array with a value
arr.fill(0);

// swap contents with another array of the same type and size
array<int, 5> arr2 = {6, 7, 8, 9, 10};
arr.swap(arr2);
```

### Size and capacity operations

```cpp
array<int, 5> arr = {1, 2, 3, 4, 5};
cout << arr.size() << endl;     // 5
cout << arr.empty() << endl;    // false
```

### Sorting an array

```cpp
array<int, 5> arr = {3, 1, 4, 2, 5};

// sort in ascending order
sort(arr.begin(), arr.end());
// sort in descending order using `greater`
sort(arr.begin(), arr.end(), greater<int>());
// sort in descending order using a lambda function
sort(arr.begin(), arr.end(), [](int a, int b) { return a > b; });
```

## Considerations

- `std::array` is a fixed-size container, meaning its size must be known at compile time and cannot be changed.
- `std::array` has zero overhead compared to C-style arrays while providing a safer interface.
- Unlike C-style arrays, `std::array` knows its own size and can be safely passed to and returned from functions.
- `std::array` is a contiguous container, meaning that its elements are stored in a contiguous block of memory.

## See also

- [std::vector](containers/vector)

## References

- [cppreference.com - array](https://en.cppreference.com/w/cpp/container/array)
