# 使用 Taihe 进行 interface inherit 相关开发

## 简介

Taihe支持interface继承interface，@class interface继承interface，需要用户对[interface](./use-taihe-about-interface.md)和[class](./use-taihe-about-class.md)有基础的了解。

## 基本概念

Taihe IDL 语法支持接口单继承和多继承，例如，interface A: B, C {} 表示 interface A 继承了 interface B 和 interface C。

Taihe 相关代码示例

```rust
interface IBase {
    getId(): String;
    setId(s: String): void;
}
interface IShape: IBase {
    calculateArea(): f64;
}
@class
interface IDerived: IShape {
    call(): void;
}
```

以下是对应的 ets 代码

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
    native _taihe_call_native(): void;
    native _taihe_calculateArea_native(): double;
    native _taihe_getId_native(): string;
    native _taihe_setId_native(s: string): void;
    constructor () {
        _taihe_createIDerived_native();
    }
    call(): void {
        return this._taihe_call_native();
    }
    calculateArea(): double {
        return this._taihe_calculateArea_native();
    }
    getId(): string {
        return this._taihe_getId_native();
    }
    setId(s: string): void {
        return this._taihe_setId_native(s);
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

function makeIBase(id: String): IBase;
function copyIBase(a: IBase, b: IBase): void;

interface IShape: IBase {
    calculateArea(): f64;
}

function makeIShape(id: String, a: f64, b: f64): IShape;

@class
interface IDerived: IShape {
    call(): void;
}

@constructor("IDerived")
@rename
function createIDerived(): IDerived;
```

### C++ 实现

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
```

Output：

```sh
new base 0x12cf718c0
ibase_1 getId:  abc
ibase_1 setId:  xyz
new base 0x12cf73510
copyIBase:  test test
new shape 0x12cf73700
makeIShape:  7.850000381469727
interface extends:  shape
interface extends set:  aaaaa
impl interface:  A A
interface extends:  aaaaa aaaaa
derived call!
d
```
