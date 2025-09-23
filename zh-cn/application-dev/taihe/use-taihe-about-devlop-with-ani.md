# 使用Taihe进行ANI协同开发

## 简介

Taihe提供Opaque类型声明外部语言对象，用于表达在Taihe中无法表达的不透明类型，并允许使用`@sts_type`注解指定该外部语言对象的具体ets类型。

## 基本概念

当有部分类型在Taihe中不可见时，可以使用Taihe的Opaque类型进行声明，在C++实现侧编写ANI代码。

```rust
function is_string(s: Opaque): bool;
```

C++实现：

```cpp
bool is_string(uintptr_t s) {
    ani_env *env = get_env();
    ani_boolean res;
    ani_class cls;
    env->FindClass("std.core.String", &cls);
    env->Object_InstanceOf((ani_object)s, cls, &res);
    return res;
}
```

`Opaque`类型在ArkTS侧对应的类型为`Object`，因此上述Taihe声明在ArkTS侧对应的声明为：

```typescript
function is_string(s: Object): boolean;
```

`Opaque`类型的使用场景通常是：某些类型完全是在ArkTS侧定义的，而在Taihe IDL中并没有对应的声明，例如：

```typescript
export interface Person {
    name: string;
    age: number;
}
```

此时，如果希望使用Taihe声明一个函数来处理`Person`类型的参数，就必须使用`Opaque`类型来作为该参数的类型。此外，为了使该类型在ArkTS侧能被正确投影为`Person`类型而非`Object`类型，我们需要使用`@sts_type`注解来修饰该类型，表示该`Opaque`类型在ArkTS侧实际对应的具体类型为`Person`：

```rust
@!sts_inject("import {Person} from 'other.subsystem';")
function processPerson(person: @sts_type("Person") Opaque): void;
```

C++实现：

```cpp
void processPerson(uintptr_t person) {
    ani_env *env = get_env();
    ani_object ani_obj = reinterpret_cast<ani_object>(person);
    ani_string name;
    ani_int age;
    env->Object_GetPropertyByName_Ref(ani_obj, "name",
                                      reinterpret_cast<ani_ref *>(&name));
    env->Object_GetPropertyByName_Int(ani_obj, "age", &age);
    ani_size len;
    env->String_GetUTF8Size(name, &len);
    char *name_utf8 = new char[len + 1];
    env->String_GetUTF8(name, name_utf8, len + 1, &len);
    std::cout << "name: " << name_utf8 << ", age: " << age << std::endl;
    delete[] name_utf8;
}
```

注：1. ANI相关开发参考[ANI文档](../ani/ani-usage-scenarios.md)。2. 注解`@sts_inject`参考[文档](./use-taihe-about-devlop-with-ets.md)。

## 使用示例

### 外部类型声明

```typescript
export interface Person {
    name: string;
    age: number;
}
```

### Taihe声明

```rust
@!sts_inject("import {Person} from 'other.subsystem';")

function is_string(s: Opaque): bool;

function processPerson(person: @sts_type("Person") Opaque): void;
```

### C++实现

```cpp
bool is_string(uintptr_t s) {
    ani_env *env = get_env();
    ani_boolean res;
    ani_class cls;
    env->FindClass("std.core.String", &cls);
    env->Object_InstanceOf((ani_object)s, cls, &res);
    return res;
}

void processPerson(uintptr_t person) {
    ani_env *env = get_env();
    ani_object ani_obj = reinterpret_cast<ani_object>(person);
    ani_string name;
    ani_int age;
    env->Object_GetPropertyByName_Ref(ani_obj, "name",
                                      reinterpret_cast<ani_ref *>(&name));
    env->Object_GetPropertyByName_Int(ani_obj, "age", &age);
    ani_size len;
    env->String_GetUTF8Size(name, &len);
    char *name_utf8 = new char[len + 1];
    env->String_GetUTF8(name, name_utf8, len + 1, &len);
    std::cout << "name: " << name_utf8 << ", age: " << age << std::endl;
    delete[] name_utf8;
}
```

### ets使用

```typescript
    console.log(extobj.is_string("hello"));
    console.log(extobj.is_string(123));

    let person: Person = {name: "John", age: 30};
    extobj.processPerson(person);
```

输出结果如下：
```sh
true
false
name: John, age: 0
```
