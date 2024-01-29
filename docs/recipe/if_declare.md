# if条件式内で変数宣言

## サンプルコード

C++17以降から、if条件内で変数を定義することができるようになった。

```cpp
if (auto i = 1 + 2; i > 2) {
  std::cout << "i is greater than 2: " << i << std::endl;
}
```

```cpp
constexpr auto threshold = 0.5;
constexpr auto e = std::numeric_limits<double>::epsilon();
if (const auto distance = std::hypot(x1 - x0, y1 - y0); std::abs(distance - threshold) <= e) {
  std::cout << "Reached Goal!" << std::endl;
}
```
