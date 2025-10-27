# 使用Taihe进行namespace相关开发

## 简介

ArkTS中以模块和命名空间来组织代码。模块用于区分不同的功能单元，而命名空间则用于在模块内对代码进行分组，避免命名冲突。Taihe通过`@!namespace`注解来支持将一个Taihe IDL文件的内容映射到ArkTS侧的指定模块和命名空间中。

## 基本概念

命名空间注解的语法为`@!namespace(<module_name>, <namespace_name>)`，这个注解放置放在文件顶层，作用于整个Taihe IDL文件。表示该文件内容在ArkTS侧对应于`<module_name>`模块的`<namespace_name>`命名空间。例如，`@!namespace("@ohos.multimedia.image", "image")`表示该文件内容在ArkTS侧对应于`@ohos.multimedia.image`模块内的`image`命名空间。

文件的第二个参数`<namespace_name>`可以有多个层级，例如`@!namespace("module1", "foo.bar")`表示该文件内容在ArkTS侧对应于`module1`模块内的`foo.bar`命名空间。另外该参数也可以省略，表示该文件内容在ArkTS侧对应于`<module_name>`模块的顶层命名空间。

一个Taihe IDL文件最多只能有一个`@!namespace`注解。在不使用该注解时，会默认使用当前Taihe IDL文件对应的[包名](./taihe-idl-reference.md#定义包)作为ArkTS侧的模块名，且对应于该模块的顶层命名空间。

推荐将Taihe文件命名为`<module_name>.<namespace_name>.ohidl`。

**`module1.ohidl`**
```rust
function module1Run(): void;
```

**`module1.foo.ohidl`**
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
可以看到`module1.ohidl`和`module1.foo.ohidl`的内容都生成在`module1.ets`文件中。

假如只需要一个`<module_name>.<namespace_name>.ohidl`的文件，无需额外创建一个空内容的`<module_name>.ohidl`文件。

**`module2.bar.ohidl`**
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

**`module1.ohidl`**
```rust
function module1Run(): void;
```

**`module1.foo.ohidl`**
```rust
@!namespace("module1", "foo")

function fooFunc(): void;
```

**`module2.bar.ohidl`**
```rust
@!namespace("module2", "bar")

function barFunc(): void;
```

### C++实现

**`module1.ohidl的C++实现`**
```cpp
void module1Run() {
    std::cout << "Module: module1" << std::endl;
}
```

**`module1.foo.ohidl的C++实现`**
```cpp
void fooFunc() {
    std::cout << "namespace: module1.foo, func: foo" << std::endl;
}
```

**`module2.bar.ohidl的C++实现`**
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
