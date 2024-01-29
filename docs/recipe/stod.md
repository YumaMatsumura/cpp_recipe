# 文字列から数値への変換

## stod, stol関数を使用する

<b>基本的な使い方</b>

```cpp
double a = std::stod("100.0");  // 100.0
double b = std::stod("-100.0"); // -100.0
double c = std::stod(5e3);      // 5000.0
double d = std::stod("abc");    // throws an exception (std::invalid_argument)
double e = std::stod("3hoge");  // 3.0 (1)
```

1. 途中まで数値のものは数値部分が出力される

<b>進数指定</b>

```cpp
double a = std::stod("0xFF");              // 0 （10進数として認識）
double b = std::stod("0xFF", nullptr, 16); // 255 (16進数として認識)
double c = std::stod("01101", nullptr, 2); // 13 (2進数として認識) (1)
```

1. 0bで始まる数値は2進数として認識できない。

<b>数値として解釈できない文字の情報を格納</b>

```cpp
size_t idx = 0;
std::string s = "10%";
double a = std::stod(s, &idx);      // idxに数値として認識できない文字の最初のインデックス番号が格納
if (idx != a.size()) {
  std::cout << s[idx] << std::endl; // %
}
```

以下、全文字列が数値として認識できるかチェックする関数の実装例である。

```cpp
bool isNumericalString(const std::string & s)
{
  size_t idx = 0;
  std::stod(s, &idx);
  if (s.size() == idx) {
    true;
  }
  return false;
}
```

## 参考

- [https://qiita.com/yohm/items/234e8b02a0fc96d3fa92](https://qiita.com/yohm/items/234e8b02a0fc96d3fa92)
