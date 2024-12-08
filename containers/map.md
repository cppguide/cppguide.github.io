# Introduction to std::map

The `std::map` is a container that stores elements in a key-value pair. The key is unique and the value is associated with the key. The elements are stored in a sorted order based on the keys.

The type of the key should be comparable, i.e. the `operator<` should be defined for the key type.

## Example Usage

Before using `std::map`, make sure to include the `<map>` header:

```cpp
#include <map>
```

If you don't want to use `std::` as prefix, you can alias it:

```cpp
using namespace std;
```

NOTE: The following examples will use the alias `map` for `std::map` and will not include the header.

### Creating a map

#### Default constructor

```cpp
map<int, string> m;
map<string, int> m2;
```

#### Initializer list constructor

```cpp
map<int, string> m = {{1, "one"}, {2, "two"}, {3, "three"}};
```

#### Copy constructor

```cpp
map<int, string> m2(m);
```

### Accessing elements

```cpp
map<int, string> m = {{1, "one"}, {2, "two"}, {3, "three"}};
cout << m[1] << endl; // one  if the key is present, otherwise it adds the key with a default constructed value
cout << m.at(2) << endl; // two if the key is present, otherwise it throws an exception
```

### Iterating over a map

```cpp
// range-based for loop using structured bindings since C++17 
for (const auto& [key, value] : m) {
    cout << key << " -> " << value << endl;
}

// if you need to modify the value, you can use auto&
for (auto &[key, value] : m) {
    if (key == 2) {
        value = "TWO";
    }
}
// or non-const iterator
for (auto it = m.begin(); it != m.end(); ++it) {
    it->second = "modified";
}

// const iterator
for (auto it = m.cbegin(); it != m.cend(); ++it) {
    cout << it->first << " -> " << it->second << endl;
}

// const reverse iterator
for (auto it = m.crbegin(); it != m.crend(); ++it) {
    cout << it->first << " -> " << it->second << endl;
}
```

### Modifying a map

```cpp
// if the added key is not a key in the map, it is added, otherwise the value is updated. 
m.insert({4, "four"}); 
m.insert(make_pair(5, "five"));
m.insert(pair<int, string>(6, "six"));
m[7] = "seven";
```

### Removing elements

```cpp
m.erase(3);
m.erase(m.begin());
m.clear(); // removes all elements from the map
```

### Finding an element

```cpp
auto it = m.find(2); // returns an iterator to the element with the key 2 if it exists, otherwise it returns m.end()
if (it != m.end()) {
    cout << it->first << " -> " << it->second << endl;
}
```

### Counting elements with a given key

```cpp
size_t count = m.count(2); // returns 1 if the key is present, otherwise 0
```

### Checking if a map is empty

```cpp
bool is_empty = m.empty(); // returns true if the map is empty, otherwise false
```

### Getting the size of a map

```cpp
size_t size = m.size(); // returns the number of elements in the map
```

### Checking if a map contains a key

```cpp
bool contains = m.count(2) > 0;
bool contains2 = m.find(2) != m.end();
```

### Storing a custom object as a key

```cpp
class CustomKey {
public:
    int id;
    string name;
    CustomKey(int id, string name) : id(id), name(name) {}
    bool operator<(const CustomKey& other) const {
        return id < other.id;
    }
};

map<CustomKey, string> m; // operator< is required for the key type
```

## Considerations

- Maps are typically implemented as red-black trees, which means that the elements are stored in a sorted order based on the keys. This results in O(log n) time complexity for most operations.
- If you need to store elements in a specific order, you should use `std::map`.
- If you need to store elements in a random order and a faster lookup time, you should use `std::unordered_map`.


## References

- [cppreference.com - map](https://en.cppreference.com/w/cpp/container/map)
