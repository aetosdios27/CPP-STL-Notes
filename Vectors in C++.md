## Introduction

Vectors are dynamic arrays in C++ that can grow and shrink in size automatically. They are part of the **STL (Standard Template Library)** and are defined in the `<vector>` header. Vectors are widely used in **competitive programming (CP)** due to their flexibility and fast operations.

## Declaration and Initialization

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> v1;            // Empty vector
    vector<int> v2(5);         // Vector of size 5 with default values (0 for int)
    vector<int> v3(5, 10);     // Vector of size 5 initialized with 10
    vector<int> v4 = {1, 2, 3, 4, 5}; // Vector with initializer list
    return 0;
}
```

## Important Operations (CP Specific)

### Adding and Removing Elements

```cpp
v.push_back(10);  // O(1) Adds 10 to the end
v.pop_back();     // O(1) Removes the last element
```

### Accessing Elements

```cpp
int x = v[0];      // O(1) Direct access (no bounds checking)
int y = v.at(2);   // O(1) Safe access (throws exception if out of bounds)
```

### Size and Capacity

```cpp
int size = v.size();        // O(1) Number of elements
int capacity = v.capacity(); // O(1) Current allocated storage
```

## Efficient Traversal

### Using a range-based for-loop

```cpp
for (int num : v) {
    cout << num << " ";
}
```

### Using iterators

```cpp
for (auto it = v.begin(); it != v.end(); ++it) {
    cout << *it << " ";
}
```

## Sorting for CP

Sorting is **crucial** in CP problems.

```cpp
#include <algorithm>
sort(v.begin(), v.end()); // O(N log N) Sorts in ascending order
sort(v.rbegin(), v.rend()); // O(N log N) Sorts in descending order
```

## Removing Duplicates Efficiently

```cpp
sort(v.begin(), v.end());
v.erase(unique(v.begin(), v.end()), v.end());
```

This is useful for CP problems requiring unique values after sorting.

## Erasing Elements (Efficient Deletion)

```cpp
v.erase(v.begin());         // O(N) Removes first element
v.erase(v.begin() + 2);     // O(N) Removes element at index 2
```

## Inserting Elements

```cpp
v.insert(v.begin() + 2, 50); // O(N) Inserts 50 at index 2
```

## 2D Vectors (CP Use Case)

```cpp
vector<vector<int>> matrix(3, vector<int>(4, 0));
```

This creates a **3x4 matrix** initialized with 0.

## Best Practices for CP

1. **Use reserve() for large vectors** to prevent frequent reallocation.

```cpp
v.reserve(1000000); // Preallocates memory for 1M elements
```

2. **Prefer vector over array unless fixed size is known.**
3. **Use `clear()` instead of reassigning a new vector to save memory.**
4. **Use `shrink_to_fit()` after clearing a large vector.**

```cpp
v.clear();
v.shrink_to_fit();
```

## Summary

- `push_back()` and `pop_back()` are O(1)
- `sort()` is O(N log N)
- `erase()` and `insert()` are O(N), avoid excessive use
- **Use `reserve()` for better performance in large constraints**
- **Removing duplicates efficiently with `unique()`**

Vectors are powerful and essential for CP, allowing flexible and efficient manipulation of sequences. Mastering them is key to solving many problems efficiently!