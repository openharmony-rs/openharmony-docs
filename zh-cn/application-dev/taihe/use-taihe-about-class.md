# 使用 Taihe 进行 class 相关开发

## 简介

使用 Taihe 进行 class 相关开发时，可以使用 @class 注解修饰 [struct](./use-taihe-about-struct.md) 或 [interface](./use-taihe-about-interface.md)，纯数据类使用 @class struct，含有方法的类需使用 @class interface。

## 基本概念

Taihe 相关代码示例

```rust
@class
struct Teacher {
    @readonly name: String;
    age: i32;
}
function create_teacher(): Teacher;
function process_teacher(a: Teacher): Teacher;
```

以下是对应的 ets 代码

```typescript
native function _taihe_process_student_native(a: Student): Student;
native function _taihe_create_teacher_native(): Teacher;
export class Teacher {
    readonly name: string;
    age: int;
    constructor(
        name: string,
        age: int,
    )
    {
        this.name = name;
        this.age = age;
    }
    // 在生成的 class 中会自动生成一个默认的 constructor 函数
}
export function create_teacher(): Teacher {
    return _taihe_create_teacher_native();
}
export function process_teacher(a: Teacher): Teacher {
    return _taihe_process_teacher_native(a);
}
```

对于以上的接口声明，如果不添加 @class 注解，那么在 ets 侧会默认投影成 `interface Teacher`。如果需要将其投影为 `class` 则需使用 @class 注解，使其在 ets 侧直接生成为 `class Teacher`。

使用 @constructor 注解可以给对应的 class 添加构造函数，它仅对 @class interface 有效。

注意，使用 @class 时通常需要提供构造函数，除非确认无需在 ets 层使用 new 实例化。

使用@static注解会给对应的class添加静态方法，它仅对@class interface有效。[@rename 注解](./use-taihe-about-rename.md)会改变ets侧方法名，使用@rename("<new_name>")会使得ets侧方法名修改为new_name, 当其不带参数时会在ets侧生成匿名函数。

注意，根据 ets 规范，当一个 class 只有一个构造函数时，该函数应该为匿名构造函数，所以应该使用 @rename。

Taihe 相关代码示例

```rust
@class
interface IBase {
    get(): String;
    set(a: String): void;
}

@static("IBase")
function sumSync(a: i32, b: i32): i32;

@constructor("IBase")
@rename
function getIBase(name: String): IBase;
```

以下是对应的 ets 代码

```typescript
native function _taihe_sumSync_native(a: int, b: int): int;
native function _taihe_getIBase_native(name: string): IBase;
export class IBase {
    // 匿名构造函数
    constructor (name: string) {
        _taihe_getIBase_native(name);
    }
    // 静态方法
    static sumSync(a: int, b: int): int {
        return _taihe_sumSync_native(a, b);
    }
    native _taihe_get_native(): string;
    native _taihe_set_native(a: string): void;
    get(): string {
        return this._taihe_get_native();
    }
    set(a: string): void {
        return this._taihe_set_native(a);
    }
}
```

## 使用示例

### Taihe 声明

```rust
@class
struct Teacher {
    @readonly name: String;
    age: i32;
}
function create_teacher(): Teacher;
function process_teacher(a: Teacher): Teacher;

@class
interface IBase {
    get(): String;
    set(a: String): void;
}

@static("IBase")
function sumSync(a: i32, b: i32): i32;

@constructor("IBase")
@rename
function getIBase(name: String): IBase;
```

### C++ 实现

```cpp
Teacher create_teacher() {
  return Teacher{"Rose", 25};
}

Teacher process_teacher(Teacher const &a) {
  return {a.name + " teacher", a.age + 15};
}

struct AuthorIBase {
  taihe::string name;

  explicit AuthorIBase(taihe::string_view name) : name(name) {}

  AuthorIBase(taihe::string_view name, taihe::string_view t) : name(t) {}

  ~AuthorIBase() {}

  taihe::string get() {
    return name;
  }

  void set(taihe::string_view a) {
    this->name = a;
    return;
  }
};

IBase getIBase(taihe::string_view name) {
  return taihe::make_holder<AuthorIBase, IBase>(name);
}

int32_t sumSync(int32_t a, int32_t b) {
  return a * b;
}
```

### ets 侧使用

```typescript
let teacher: Teacher = new Teacher("Jony", 30);
let pro_teacher = process_teacher(teacher);
console.log("process teacher:", pro_teacher.name, pro_teacher.age);

const result = IBase.sumSync(10, 20);
console.log("sumSync result:", result);

let test = new IBase("hello");
console.log("new IBase get:", test.get());
```

Output：

```sh
process teacher: Jony teacher 45
sumSync result: 200
new IBase get: hello
```
