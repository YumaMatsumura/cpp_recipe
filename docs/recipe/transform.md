# vectorの要素全てに処理をする

## std::transform

全ての要素2倍するコードの例を以下に示す。

<b>std::transformを使わない場合</b>

```cpp
const std::vector<int> x{1, 9, 8, 6, 12, 14};
std::vector<int> y(x.size());

for (const auto e : x) {
  y.emplace_back(e * 2);
}
```

<b>std::transformを使う場合</b>

```cpp
const std::vector<int> x{1, 9, 8, 6, 12, 14};
std::vector<int> y(x.size());

std::transform(
  x.cbegin(), x,cend(), y.begin(),
  [](const int e) {
    return e * 2;
  });
```

その他の例を以下に示す。

```cpp
std::vector<int> v = {3, 1, 4};
std::vector<std::string> result;

std::transform(
  v.begin(), v.end(), std::back_inserter(result),
  [](int x) {
    return std::to_string(x * 2);
  });
```

## 参考

- [https://qiita.com/IgnorantCoder/items/3101d6276e9bdddf872c](https://qiita.com/IgnorantCoder/items/3101d6276e9bdddf872c)
