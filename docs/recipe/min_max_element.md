# vectorの最小値・最大値を返す

## min_element, max_element

```cpp
std::vector<int> v1 = {3, 1, 4};

const auto min_iter = std::min_element(v1.begin(), v1.end()); // (1)!
const auto max_iter = std::max_element(v1.begin(), v1.end());

const int min_value = *min_iter; // 1
const int max_value = *max_iter; // 4

std::size_t min_index = std::distance(v1.begin(), min_iter);  // 1 (2)
std::size_t max_index = std::distance(v1.begin(), max_iter);  // 2
```

1. 返り値はイテレータ（std::vector<int>::iterator）。
2. distanceでそのイテレータのインデックス番号を取得できる。

## 参考

- [https://cpprefjp.github.io/reference/algorithm/max_element.html](https://cpprefjp.github.io/reference/algorithm/max_element.html)
- [https://cpprefjp.github.io/reference/iterator/distance.html](https://cpprefjp.github.io/reference/iterator/distance.html)
- [https://qiita.com/shirakawa4756/items/f4cc65c6b2b412b10c0c](https://qiita.com/shirakawa4756/items/f4cc65c6b2b412b10c0c)
