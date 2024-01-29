# Pimpl（ピーインプル）イディオム

## Pimpl

pointer to implementationの略。
classのprivateにしても外部から閲覧できてしまう。これを解決するのがpimpl。

## サンプルコード

<b>pimpl導入前のコードについて</b>

```cpp title="hello_world.h"
class HelloWorld
{
public:
  HelloWorld();
  ~HelloWorld();

private:
  void printHelloWorld();
};
```

```cpp title="hello_world.cpp"
#include "hello_world.h"

HelloWorld::HelloWorld()
{
  printHelloWorld();
}

HelloWorld::~HelloWorld()
{
}

void HelloWorld::printHelloWorld()
{
  std::cout << "Hello world!" << std::endl;
}
```

<b>pimpl導入後のコードについて</b>

```cpp title="hello_world.h"
class HelloWorld
{
public:
  HelloWorld();
  ~HelloWorld();

private:
  class Impl;
  std::unique_ptr<Impl> hello_world; // (1)!
};
```

1. privateでclass宣言

```cpp title="hello_world.cpp"
#include "hello_world.h"

class HelloWorld::Impl // (1)!
{
public:
  void printHelloWorld();
};

HelloWorld::HelloWorld()
: hello_world(new HelloWorld::Impl()) // (2)!
{
  hello_world->printHelloWorld();
}

HelloWorld::~HelloWorld()
{
}

void HelloWorld::Impl::printHelloWorld() // (3)!
{
  std::cout << "Hello world!" << std::endl;
}
```

1. Implクラスの作成。publicにもともとprivateなメンバ関数を実装。
2. Implクラスをコンストラクタでインスタンス化。
3. もともとprivateで行いたかった実装をこちらに記述。

## 参考

- [https://qiita.com/CASL0/items/0f9889851dcf8ae22665](https://qiita.com/CASL0/items/0f9889851dcf8ae22665)
- [https://qiita.com/ashdik/items/b6b9924113f7e8d531cf](https://qiita.com/ashdik/items/b6b9924113f7e8d531cf)
