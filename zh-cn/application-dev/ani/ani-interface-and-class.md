# 接口和类
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @fang-jinxu-->

在ANI中，接口不能直接实例化。必须在类中实现它们（类实现接口）后才能使用。

接口中的所有字段都会自动被视为属性（property）。当一个类实现一个接口时，继承的成员也会变成属性。

```ts
interface PointI {
    x: int // property - 默认生成getter & setter
    y: int // property - 默认生成getter & setter
}
class Point implements PointI {
    x: int // property - 默认生成getter & setter
    y: int // property - 默认生成getter & setter
    z: int // field    - 无默认的getter & setter
}
```

```cpp
ani_class clsPointI; ani_method ctorPointI; // 假设已初始化
ani_class clsPoint; ani_method ctorPoint;   // 假设已初始化
ani_object objPointI; ani_object objPoint;
env->Object_New(clsPointI, ctorPointI, &objPointI); // 失败
env->Object_New(clsPoint, ctorPoint, &objPoint);    // 成功
```

- 创建接口对象会失败
- 创建类对象会成功。

在ANI中，类的创建不依赖于接口，但接口对象需要类的实现。

在ArkTS代码中，接口对象可以通过对象字面量（_object literal_）表达式创建：

```ts
let p: PointI = { x: 1, y: 1 };
```

前端会自动生成一个实现了PointI接口的类。不过，该类的对象属性访问实际上是通过编译器自动生成的`getter`和`setter`方法实现的，而不是直接访问字段。

## 属性和字段

- **属性**：带有`get/set`方法声明。
- **字段**：没有`get/set`方法的属性。
- 接口中的所有属性在实现类中都会变成属性。

> **在ANI中不要混淆属性和字段函数！**
> 例如：
> - `Class_FindField`不能用于属性。
> - `Object_GetPropertyByName_Boolean`不能用于字段。

下面的代码展示了属性和字段在ArkTS声明中的区别：

```ts
interface PointI {
    x: int // property
    y: int // property
}
class Point implements PointI {
    x: int // property
    y: int // property
    z: int // field
}
```

## 访问属性
### 访问和设置属性
| 函数名 | 操作 | 描述 |
| --------------------------------- | --- | ------------------- |
| `Object_GetPropertyByName_<Type>` | get | 以原始类型检索属性   |
| `Object_SetPropertyByName_<Type>` | set | 使用原始类型设置属性 |

如果属性是引用类型，则使用`_Ref`后缀。

**示例：**

```ts
interface Person {
    name: string;
    age: int;
}

class PersonInner implements Person {
    name: string = "";
    age: int = 2;
}

native function modifyPerson(person: Person): void
```

```cpp
void ModifyPersonImpl(ani_env *env, ani_object person)
{
    static constexpr std::string_view name = "Goose";
    ani_string nameValue {};
    env->String_NewUTF8(name.data(), name.size(), &nameValue);
    ani_int ageValue = 42;

    env->Object_SetPropertyByName_Int(person, "age", ageValue);
    env->Object_SetPropertyByName_Ref(person, "name", nameValue);

    ani_int ageValueRet = 0;
    ani_ref nameValueRet {};
    env->Object_GetPropertyByName_Int(person, "age", &ageValueRet);
    env->Object_GetPropertyByName_Ref(person, "name", &nameValueRet);
}
```

### 访问和设置字段

| 函数名 | 操作 | 描述 |
| ------------------------------ | ---- | ------------------- |
| `Object_GetFieldByName_<Type>` | 获取 | 以原始类型检索字段   |
| `Object_SetFieldByName_<Type>` | 设置 | 使用原始类型设置字段 |

**示例：**

```ts
class Person {
    name: string = "";
    age: int = 2;
    thisIsField: int = 3;
}

native function modifyPerson(person: Person): void
```

```cpp
void ModifyPersonImpl(ani_env *env, ani_object person)
{
    static constexpr std::string_view name = "Goose";
    ani_string nameValue {};
    env->String_NewUTF8(name.data(), name.size(), &nameValue);
    ani_int ageValue = 42;

    env->Object_SetFieldByName_Int(person, "age", ageValue);
    env->Object_SetFieldByName_Ref(person, "name", nameValue);

    ani_int ageValueRet = 0;
    ani_ref nameStringRet {};
    env->Object_GetFieldByName_Int(person, "age", &ageValueRet);
    env->Object_GetFieldByName_Ref(person, "name", &nameStringRet);
}
```

### 访问静态字段
| 函数名 | 操作 | 描述 |
| ----------------------------------- | ---- | ------------- |
| `Class_GetStaticFieldByName_<Type>` | 获取 | 检索静态字段值 |
| `Class_SetStaticFieldByName_<Type>` | 设置 | 设置静态字段值 |

## 调用方法

使用`Object_CallMethod_<Type>`，其中`<Type>`表示返回类型。

**示例：**

```ts
// example.ets
class Foo {
    native nativeFunc(): void;
    managedFunc(): void {
        console.println("Print in managedFunc");
    }
}
```

```cpp
static void NativeFuncImpl(ani_env *env, ani_object obj) {
    ani_method managedFunc {};
    ani_type result {};

    static constexpr const char *className = "example.Foo";
    ani_class cls {};
    if (ANI_OK != env->FindClass(className, &cls)) {
        std::cerr << "Not found '" << className << "'" << std::endl;
        return;
    }
    if (ANI_OK != env->Class_FindMethod(cls, "managedFunc", ":", &managedFunc)) {
        std::cerr << "Class_FindMethod Failed" << std::endl;
        return;
    }
    std::cout << "Print in Native Func" << std::endl;
    env->Object_CallMethod_Void(obj, managedFunc);
}
```
## 可选方法作为可选参数

ArkTS 1.2不直接支持可选方法，可使用可选函数参数代替。

**示例：**
```ts
// example.ets
class OptionalClass {
    fn?: (a: double, b: double) => double = (a: double, b: double) => a + b;
}
native function callOptionalFn(opt: OptionalClass, a: double, b: double): double

let opt = new OptionalClass();
console.info(opt.fn(1.0, 2.0));
console.info(callOptionalFn(opt, 1.0, 2.0));
```

```cpp
ani_double CallOptionalFnImpl(ani_env *env, ani_object opt, ani_double val1, ani_double val2)
{
    ani_ref fnRef {};
    env->Object_GetFieldByName_Ref(opt, "fn", &fnRef);

    // Note: functional objects always accept and return boxed primitives
    std::array<ani_ref, 2> args = {createDouble(env, val1), createDouble(env, val2)};
    ani_ref fnReturnVal {};
    env->FunctionalObject_Call(static_cast<ani_fn_object>(fnRef), args.size(), args.data(), &fnReturnVal);

    ani_double result {};
    env->Object_CallMethodByName_Double(static_cast<ani_object>(fnReturnVal), "toDouble", ":d", &result);
    return result;
}
```

## Native指针包装与释放

当ArkTS对象需要关联C++侧对象实例时，可以在ArkTS类中保存一个`long`字段，用于存放native指针。C++侧创建对象后，将指针转换为`ani_long`写入该字段；后续native实例方法再读取该字段，并转换回对应的C++指针使用。

这种方式常用于把C++对象生命周期挂到ArkTS对象上。需要注意，`long`字段只保存指针值，本身不会自动释放native资源；应配合`FinalizationRegistry`或显式释放接口，在ArkTS对象不再使用时清理C++对象。

示例：[ani_wrap_native_ptr.ets](https://gitcode.com/LeechyLiang/ani_cookbook/blob/master/ani_wrap_native_ptr/ani_wrap_native_ptr.ets)

