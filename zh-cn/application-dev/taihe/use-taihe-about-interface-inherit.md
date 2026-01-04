# 使用Taihe进行interface inherit相关开发

## 简介

Taihe支持interface继承interface，@class interface继承interface，@class interface继承@class interface，需要用户对[interface](./use-taihe-about-interface.md)和[class](./use-taihe-about-class.md)有基础的了解。

## 基本概念

Taihe IDL 语法支持接口单继承和多继承，例如，interface A: B, C {} 表示 interface A 继承了 interface B 和 interface C。

以下述代码为例，其中包含：
- interface继承interface：IShape继承IBase；
- @class interface继承interface：IDerived继承IShape；
- @class interface继承@class interface：IFancy继承IDerived。

Taihe相关代码示例：

```rust
interface IBase {
    getId(): String;
    setId(s: String): void;
}

interface IShape: IBase {
    calculateArea(): f64;
}

// @class interface继承interface
@class
interface IDerived: IShape {
    call(): void;
}

// @class interface继承@class interface
@class
interface IFancy: IDerived {
    show(): void;
}
```

以下是Taihe生成的ets代码（简化版）：

因为存在多级继承，每个类会实现自身、基类、间接基类的方法。

```typescript
export interface IBase {
    getId(): string;
    setId(s: string): void;
}

// interface 继承 interface 表现为 extends
export interface IShape extends IBase {
    calculateArea(): double;
}

// @class interface 继承 interface 表现为 implements
export class IDerived implements IShape {
    // 拷贝构造函数
    constructor(other: IDerived) {
      // 调用Taihe生成的拷贝构造函数
    }

    // 以下方法供开发者使用，从而调用native侧实现
    call(): void {
        // 调用native侧call
    }
    calculateArea(): double {
        // 调用native侧calculateArea
    }
    getId(): string {
        // 调用native侧getId
    }
    setId(s: string): void {
        // 调用native侧setId
    }
}

// @class interface 继承 @class interface 表现为 extends
export class IFancy extends IDerived {
    // 拷贝构造函数
    constructor(other: IFancy) {
        // 调用Taihe生成的拷贝构造函数
    }

    // 以下方法供开发者使用，从而调用native侧实现
    show(): void {
        // 调用native侧show
    }
    call(): void {
        // 调用native侧call
    }
    calculateArea(): double {
        // 调用native侧calculateArea
    }
    getId(): string {
        // 调用native侧getId
    }
    setId(s: string): void {
        // 调用native侧setId
    }
}
```

## 使用示例

### Taihe 声明

```rust
interface IBase {
    getId(): String;
    setId(s: String): void;
}

interface IShape: IBase {
    calculateArea(): f64;
}

// 自定义的工具函数
function makeIBase(id: String): IBase;
function copyIBase(a: IBase, b: IBase): void;
function makeIShape(id: String, a: f64, b: f64): IShape;

@class
interface IDerived: IShape {
    call(): void;
}

@class
interface IFancy: IDerived {
    show(): void;
}

// 为类自定义默认构造函数，详见class文档
@constructor("IDerived")
@rename
function createIDerived(): IDerived;

@constructor("IFancy")
@rename
function createIFancy(): IFancy;
```

### C++ 实现

用户的native实现：

```cpp
class Base {
protected:
  ::taihe::string id;

public:
  Base(::taihe::string_view id) : id(id) {
    std::cout << "new base " << this << std::endl;
  }

  ~Base() {
    std::cout << "del base " << this << std::endl;
  }

  ::taihe::string getId() {
    return id;
  }

  void setId(::taihe::string_view s) {
    id = s;
    return;
  }
};

class Shape {
protected:
  ::taihe::string id;
  float a;
  float b;

public:
  Shape(::taihe::string_view id, float a, float b) : id(id), a(a), b(b) {
    std::cout << "new shape " << this << std::endl;
  }

  ~Shape() {
    std::cout << "del shape " << this << std::endl;
  }

  ::taihe::string getId() {
    return id;
  }

  void setId(::taihe::string_view s) {
    id = s;
    return;
  }

  float calculateArea() {
    return a * b;
  }
};

class Derived {
protected:
  ::taihe::string id = "d";
  float a = 1;
  float b = 2;

public:
  void call() {
    std::cout << "derived call!" << std::endl;
  }

  double calculateArea() {
    return a * b;
  }

  ::taihe::string getId() {
    return id;
  }

  void setId(::taihe::string_view s) {
    this->id = s;
    return;
  }
};

class Fancy {
protected:
  ::taihe::string id = "f";
  float a = 3;
  float b = 4;
public:
  void call() {
    std::cout << "fancy call!" << std::endl;
  }

  double calculateArea() {
    return a * b;
  }

  ::taihe::string getId() {
    return id;
  }
  
  void setId(::taihe::string_view s) {
    this->id = s;
    return;
  }

  void show() {
    std::cout << "Area: " << calculateArea() << std::endl;
  }
};

IBase makeIBase(::taihe::string_view id) {
  return ::taihe::make_holder<Base, IBase>(id);
}

void copyIBase(weak::IBase a, weak::IBase b) {
  a->setId(b->getId());
  return;
}

IShape makeIShape(::taihe::string_view id, double a, double b) {
  return ::taihe::make_holder<Shape, IShape>(id, a, b);
}

IDerived createIDerived() {
  return taihe::make_holder<Derived, IDerived>();
}

IFancy createIFancy() {
  return taihe::make_holder<Fancy, IFancy>();
}
```

### ets 侧使用

```typescript
class BaseImpl implements IBase {
  id: string;
  constructor(id: string) {
    this.id = id;
  }
  getId(): string {
    return this.id;
  }
  setId(id: string): void {
    this.id = id;
    return;
  }
}

// 创建父类接口
let ibase_1 = makeIBase("abc");
// 调用父类声明方法
console.log("ibase_1 getId: ", ibase_1.getId());

ibase_1.setId("xyz");
console.log("ibase_1 setId: ", ibase_1.getId());

let ibase_2 = makeIBase("test");
copyIBase(ibase_1, ibase_2);
console.log("copyIBase: ", ibase_1.getId(), ibase_2.getId());

// 创建子类接口
let ishape_1 = makeIShape("shape", 3.14, 2.5);
// 子类接口调用子类声明方法
console.log("makeIShape: ", ishape_1.calculateArea());
// 子类接口调用父类声明方法
console.log("interface extends: ", ishape_1.getId());

ishape_1.setId("aaaaa");
console.log("interface extends set: ", ishape_1.getId());

let a: BaseImpl = new BaseImpl("A");
let b: BaseImpl = new BaseImpl("B");
copyIBase(b, a);
console.log("impl interface: ", a.getId(), b.getId());

// 子类接口实例赋值给父类接口参数
copyIBase(ibase_1, ishape_1);
console.log("interface extends: ", ibase_1.getId(), ishape_1.getId());

let d = new IDerived();
d.call();
// 子类接口调用父类声明方法
console.log(d.getId());

let f = new IFancy();
f.show();
// 子类接口调用父类声明方法
f.call();
console.log(f.getId());
```

Output：

```sh
new base 0x1359de080
ibase_1 getId:  abc
ibase_1 setId:  xyz
new base 0x1359e09a0
copyIBase:  test test
new shape 0x1359e0bd0
makeIShape:  7.850000381469727
interface extends:  shape
interface extends set:  aaaaa
impl interface:  A A
interface extends:  aaaaa aaaaa
derived call!
d
Area: 12
fancy call!
f
```
