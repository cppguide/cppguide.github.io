# Introduction to std::vector

The `std::vector` is a sequence container in the C++ Standard Library that encapsulates dynamic size arrays. It is part of the `<vector>` header and provides a way to manage a collection of elements that can grow and shrink in size dynamically.

## Example Usage

Before using `std::vector`, make sure to include the `<vector>` header:

```cpp
#include <vector>
```

If you don't want to use `std::` as prefix, you can alias it:

```cpp
using namespace std;
```

NOTE: The following examples will use the alias `vector` for `std::vector` and don't include the header.

### Creating a vector

#### Default constructor

```cpp
vector<int> vec;
```

#### Initializer list constructor

```cpp
vector<int> vec2 = {1, 2, 3, 4, 5};
```

#### Fill constructor

```cpp
// 10 elements, each initialized to 0
vector<int> vec3(10, 0);
```

#### Copy constructor

```cpp
vector<int> vec4(vec2);
```

#### Range constructor

```cpp
vector<int> vec5(vec2.begin(), vec2.end());
// Partial range constructor
vector<int> vec6(vec2.begin(), vec2.begin() + 3);
```

#### Move constructor

```cpp
vector<int> vec7(std::move(vec5));
```

### Accessing elements

```cpp
vector<int> vec = {1, 2, 3, 4, 5};
// no bounds checking
cout << vec[0] << endl; // 1
// with bounds checking, throws an exception if the index is out of bounds
cout << vec.at(0) << endl; // 1

// first element
cout << vec.front() << endl; // 1
// last element
cout << vec.back() << endl; // 5
```

### Iterating over a vector

```cpp
vector<int> vec = {1, 2, 3, 4, 5};
// range-based for loop with const reference
for (const auto& elem : vec) {
    cout << elem << " ";
}
// using const iterators
for (auto it = vec.cbegin(); it != vec.cend(); ++it) {
    cout << *it << " ";
}
// using reverse const iterators
for (auto it = vec.crbegin(); it != vec.crend(); ++it) {
    cout << *it << " ";
}

// using non-const iterators
for (auto it = vec.begin(); it != vec.end(); ++it) {
    cout << *it << " ";
}
// using reverse non-const iterators
for (auto it = vec.rbegin(); it != vec.rend(); ++it) {
    cout << *it << " ";
}
// range-based for loop with non-const reference
for (auto& elem : vec) {
    cout << elem << " ";
}
```

### Modifying a vector

```cpp
vector<int> vec;
// Reserve 10 elements, to avoid reallocations if the size is known beforehand
vec.reserve(10);
// add an element to the end
vec.push_back(6);
// remove the last element
vec.pop_back();

// insert an element at the beginning
vec.insert(vec.begin(), 0);
// insert an element at the end
vec.insert(vec.end(), 7);
// insert an element at the second position
vec.insert(vec.begin() + 1, 2);
// insert 3 elements of value 8 at the third position
vec.insert(vec.begin() + 2, 3, 8);
// insert elements from another vector at the fourth position
vector<int> vec2 = {9, 10};
vec.insert(vec.begin() + 3, vec2.begin(), vec2.end());

// erase the first element
vec.erase(vec.begin());
// erase the last element
vec.erase(vec.end() - 1);
// erase the second and third elements
vec.erase(vec.begin() + 1, vec.begin() + 3);

// resize the vector to 10 elements
vec.resize(10);

// clear the vector
vec.clear();
```

### Sorting a vector

```cpp
vector<int> vec = {3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5};

// sort in ascending order
sort(vec.begin(), vec.end());
// sort in descending order using `greater`
sort(vec.begin(), vec.end(), greater<int>());
// sort in descending order using a lambda function
sort(vec.begin(), vec.end(), [](int a, int b) { return a > b; });
```

## Considerations

- `vector` is a contiguous container, meaning that its elements are stored in a contiguous block of memory.
- `vector` is a dynamic array, meaning that its size can change at runtime. If the size is known beforehand, reserve the memory to avoid reallocations.

## References

- [cppreference.com - vector](https://en.cppreference.com/w/cpp/container/vector)
