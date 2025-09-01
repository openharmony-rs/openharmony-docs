# 使用 Taihe 进行 namespace 相关开发

## 简介

命名空间（namespace）可以提供独立作用域，避免不同模块同名标识符的命名冲突。

在 Taihe 中，使用注解 `@!namespace` 可以为 Taihe 声明文件生成的 ets 代码添加一个命名空间。

## 基本概念

命名空间注解的语法为 `@!namespace(<module_name>, <namespace_name>)`，表示该文件内容属于 `<module_name>` 模块的 `<namespace_name>` 命名空间。注解用于 Taihe 文件，一个 Taihe 文件只能使用一个 `@!namespace`，一个 module 里有多个 namespace 的情况下需要将每个 namespace 写到单独的 Taihe 文件中。

推荐将 Taihe 文件命名为 <module_name>.<namespace_name>.taihe。

特殊用法：

可以使用 `@!namespace(<module_name>)`，生成的 ets 文件的文件名将更改为 `<module_name>`。

**`module1.taihe`**
```rust
function module1Run(): void;
```

**`module1.foo.taihe`**
```rust
@!namespace("module1", "foo")

function fooFunc(): void;
```

**生成`module1.ets`**
```typescript
native function _taihe_module1Run_native(): void;
export function module1Run(): void {
    return _taihe_module1Run_native();
}
function _taihe_module1Run_reverse(): void {
    return module1Run();
}
export namespace foo {
    native function _taihe_fooFunc_native(): void;
    export function fooFunc(): void {
        return _taihe_fooFunc_native();
    }
    function _taihe_fooFunc_reverse(): void {
        return fooFunc();
    }
}
```
可以看到 `module1.taihe` 和 `module1.foo.taihe` 的内容都生成在 `module1.ets` 文件中。

假如只需要一个 `<module_name>.<namespace_name>.taihe` 的文件，无需额外创建一个空内容的 `<module_name>.taihe` 文件。

**`module2.bar.taihe`**
```rust
@!namespace("module2", "bar")

function barFunc(): void;
```

**生成`module2.ets`**
```typescript
export namespace bar {
    native function _taihe_barFunc_native(): void;
    export function barFunc(): void {
        return _taihe_barFunc_native();
    }
    function _taihe_barFunc_reverse(): void {
        return barFunc();
    }
}
```

## 使用示例

### Taihe声明

**`module1.taihe`**
```rust
function module1Run(): void;
```

**`module1.foo.taihe`**
```rust
@!namespace("module1", "foo")

function fooFunc(): void;
```

**`module2.bar.taihe`**
```rust
@!namespace("module2", "bar")

function barFunc(): void;
```

### C++实现

**`module1.taihe 的 C++ 实现`**
```cpp
void module1Run() {
    std::cout << "Module: module1" << std::endl;
}
```

**`module1.foo.taihe 的 C++ 实现`**
```cpp
void fooFunc() {
    std::cout << "namespace: module1.foo, func: foo" << std::endl;
}
```

**`module2.bar.taihe 的 C++ 实现`**
```cpp
void barFunc() {
    std::cout << "namespace: module2.bar, func: bar" << std::endl;
}
```

### ets使用

```typescript
Module1.module1Run();
Module1.foo.fooFunc();
Module2.bar.barFunc();
```

输出结果如下：

```sh
Module: module1
namespace: module1.foo, func: foo
namespace: module2.bar, func: bar
```
