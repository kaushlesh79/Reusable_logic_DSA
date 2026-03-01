### Comparator Sort Function

```cpp
sort(intervals.begin(), intervals.end(), [](vector<int>& a, vector<int>& b) {
    return a[0] < b[0];
});
