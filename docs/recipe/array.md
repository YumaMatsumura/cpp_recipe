# 固定長配列

## std::array

arrayはコンパイル時に要素数を決めるため、実行時に要素数を変更することができない。

<b>可変長配列vector</b>

```cpp
std::vector<int> v(10); // 要素数10で初期化
v.at(0) = 1;

auto iter = std::begin(v);
```

<b>固定長配列array</b>

```cpp
std::array<int, 10> a; // 要素数10で変更不可
a.at(0) = 1;

auto iter = std::begin(a);
```
