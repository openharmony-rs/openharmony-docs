# 使用Taihe进行interface相关开发
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @Jemtaly; @tongdiaoZS; @m0_52007851; @zhangrunze13-->
<!--Tester: @m30041553-->
<!--Adviser: @fang-jinxu-->

## 简介

使用Taihe进行纯方法类型的接口相关开发时，可以使用interface。当接口内既包含方法，又包含数据时，可以通过@get或@set注解来说明将特定方法声明为数据的getter或setter。

## 基本概念

Taihe相关代码示例

```rust
interface ICalculator {
    add(a: i32, b: i32): i32;
    sub(a: i32, b: i32): i32;
    getLastResult(): i32;
    reset(): void;
}
```

以下是对应的ets代码

```typescript
export interface ICalculator {
  add(a: int, b: int): int;
  sub(a: int, b: int): int;
  getLastResult(): int;
  reset(): void;
}
```

使用@get或@set注解可以将一个函数设置为某个属性/变量的getter或setter，只有@get无@set时会生成readonly属性。注解可以不包含参数，此时，该方法名必须以`get`或`set`起始，对应的数据成员名会取方法名中`get`或`set`后的部分。

Taihe相关代码示例

```rust
interface Noo {
    bar(): void;
    @get getName(): String;
    @get getAge(): Optional<i32>;
    @set setAge(a: Optional<i32>): void;
}
```

以下是对应的ets代码

```typescript
export interface Noo {
  bar(): void;
  get name(): string;
  get age(): int | undefined;
  set age(a: int | undefined);
}
```

注解中也可以有参数，表示该getter或setter所对应的数据成员名，此时方法名无限制。

Taihe相关代码示例

```rust
interface Foo {
    @set("name") bar(name: String): void;
    @get("name") baz(): String;
}
```

以下是对应的ets代码

```typescript
export interface Foo {
  set name(name: string);
  get name(): string;
}
```

## 使用示例

### Taihe声明

```rust
interface ICalculator {
    add(a: i32, b: i32): i32;
    sub(a: i32, b: i32): i32;
    getLastResult(): i32;
    reset(): void;
}

function makeCalculator(): ICalculator;
function restartCalculator(a: ICalculator): void;

interface Noo {
    bar(): void;
    // 使用@get替代只读属性。
    @get getName(): String;
    // 使用@get或@set来替代属性。
    @get getAge(): Optional<i32>;
    @set setAge(a: Optional<i32>): void;
}

function GetNooIface(): Noo;
function PrintNooName(noo: Noo): String;
```

### C++实现

```cpp
class MyCalculator {
public:
    // 构造函数可以没有或有任意多个参数
    MyCalculator(int32_t init): lastResult(init){}

    // 实现interface中声明的每个方法
    int32_t add(int32_t a, int32_t b) {
        lastResult = a + b;
        return lastResult;
    }
    int32_t sub(int32_t a, int32_t b) {
        lastResult = a - b;
        return lastResult;
    }
    int32_t getLastResult() {
        return lastResult;
    }
    void reset() {
        lastResult = 0;
    }
private:
    int32_t lastResult = 0;
};

ICalculator makeCalculator() {
    // 使用make_holder将实现类和接口绑定，如有需要可传入实现类构造函数参数
    return make_holder<MyCalculator, ICalculator>(0);
}
void restartCalculator(weak::ICalculator a) {
    a->reset();
}

class MyNoo {
  string name_{"noo"};
  ::taihe::optional<int32_t> age_{::taihe::optional<int32_t>(std::in_place, 1)};

public:
  void bar() {
    std::cout << "Nooimpl: " << __func__ << std::endl;
  }

  string getName() {
    std::cout << "Nooimpl: " << __func__ << " " << name_ << std::endl;
    return name_;
  }

  ::taihe::optional<int32_t> getAge() {
    return age_;
  }

  void setAge(::taihe::optional_view<int32_t> a) {
    this->age_ = a;
    return;
  }
};

Noo GetNooIface() {
  return make_holder<MyNoo, Noo>();
}

string PrintNooName(weak::Noo noo) {
  auto name = noo->getName();
  std::cout << __func__ << ": " << name << std::endl;
  return name;
}
```

### ets侧使用

```typescript
let cal = makeCalculator();
let num1 = 1;
let num2 = 2;
let result1 = cal.add(num1, num2);
console.info("num1 + num2 = " + result1);
let result2 = cal.sub(num1, num2);
console.info("num1 - num2 = " + result2);
let result3 = cal.getLastResult();
console.info("Last calculation result: " + result3);
console.info("---restart_calculator---");
restartCalculator(cal);
let result4 = cal.getLastResult();
console.info("Last calculation result: " + result4);

let noo = getNooIface();
let name = printNooName(noo);
console.info("noo name: ", noo.name);
console.info("noo age: ", noo.age);
console.info("print noo name: ", name);
```

Output：

```sh
num1 + num2 = 3
num1 - num2 = -1
Last calculation result: -1
---restart_calculator---
Last calculation result: 0
noo name:  noo
noo age:  1
print noo name:  noo
```

## Interface C++使用方法

- `make_holder<class, interface>`是taihe提供的函数，用于将接口和实现绑定。接口的实例化可以通过`taihe::make_holder<ImplClass, Interface>(Args&&... args)`方法实现。其中`Interface`为IDL中定义的接口，`ImplClass`为用户自定义的类，该类需要实现所有接口中定义的方法，`args`为类构造函数所需参数。

- 实现侧的interface调用方法需要使用`->`调用，如以上样例中的a->reset()，不使用`.`调用。
