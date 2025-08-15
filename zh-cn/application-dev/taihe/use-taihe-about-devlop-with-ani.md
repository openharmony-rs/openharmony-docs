# 使用 Taihe 进行 ANI 协同开发

## 简介

Taihe 提供 Opaque 类型声明外部语言对象，用于表达在 Taihe 中无法表达的不透明类型，并允许使用 `@sts_type` 注解指定外部语言对象的具体 ets 类型。

## 基本概念

当有部分类型在 Taihe 中不可见时，可以使用 Taihe 的 Opaque 类型进行声明，在 C++ 实现侧编写 ANI 代码。

```rust
function is_string(s: Opaque): bool;
```

C++ 实现：

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

现存的 ArkTS 代码：

```typescript
export interface Person {
    name: string;
    age: number;
}
```

但是这部分代码没有写 Taihe 文件声明，此时可以通过 `@sts_type` 注解声明该 Opaque 在 ets 侧的类型，例如样例中的 `Person`。

```rust
@!sts_inject("import {Person} from 'other.subsystem';")
function processPerson(person: @sts_type("Person") Opaque): void;
```

C++ 实现：

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

注：1. ANI 相关开发参考 [ANI 文档](../ani/ani-usage-scenarios.md)。2. 注解 `@sts_inject` 参考 [文档](./use-taihe-about-devlop-with-ets.md)。

## 使用示例

### 现存 ArkTS 代码

```typescript
export interface Person {
    name: string;
    age: number;
}
```

我们在该示例中希望使用 Person 类型，但是没有 Person 类型相对应的 Taihe 声明时，可以使用 Opaque 类型。

### Taihe 声明

```rust
@!sts_inject("import {Person} from 'other.subsystem';")

function is_string(s: Opaque): bool;

function processPerson(person: @sts_type("Person") Opaque): void;
```

### C++ 实现

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

### ets 使用

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
