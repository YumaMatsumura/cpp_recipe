# 列挙型

## enumとenum class

C++では以下の2つの列挙型を利用できる。
例えば、以下のコードの例の場合、Poodleだと名前衝突が発生する可能性があるが、enum classではE_Dog::Poodleというように型名の指定が必要なため、名前衝突が起きなくなった。

| 種類 | スコープ有無 | 備考 |
| --- | --- | --- |
| enum | スコープなし列挙型 | C言語で利用できるenumとほぼ同じ列挙型 |
| enum class | スコープなし列挙型 | C++で新規追加された参照範囲の指定が必要な列挙型 |

<b>C言語によるenum</b>

```c
typedef enum
{
  Poodle,
  Shiba,
  Chihuahua,
  Bulldog,
} E_Dog;

int main(void) {
  E_Dog dog = Poodle;

  return 0;
}
```

<b>C++のenum class</b>

```cpp
enum class E_Dog // (1)!
{
  Poodle,
  Shiba,
  Chihuahua,
  Bulldog,
};

int main() {
  E_Dog = dog = E_Dog::Poodle;

  return 0;
}
```

1. enum classはenum structと書くこともできる。
