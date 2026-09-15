# 接口和类
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @k1ngqaquuu-->

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

// 接口对象创建失败，返回非ANI_OK状态码
ani_status status = env->Object_New(clsPointI, ctorPointI, &objPointI);
std::cerr << "Object_New PointI status: " << status << std::endl;

// 类对象创建成功，返回ANI_OK
status = env->Object_New(clsPoint, ctorPoint, &objPoint);
std::cerr << "Object_New Point status: " << status << std::endl;
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
    ani_status status = env->String_NewUTF8(name.data(), name.size(), &nameValue);
    if (status != ANI_OK) {
        // handle error and return
    }
    ani_int ageValue = 42;

    status = env->Object_SetPropertyByName_Int(person, "age", ageValue);
    if (status != ANI_OK) {
        // handle error and return
    }
    status = env->Object_SetPropertyByName_Ref(person, "name", nameValue);
    if (status != ANI_OK) {
        // handle error and return
    }

    ani_int ageValueRet = 0;
    ani_ref nameValueRet {};
    status = env->Object_GetPropertyByName_Int(person, "age", &ageValueRet);
    if (status != ANI_OK) {
        // handle error and return
    }
    status = env->Object_GetPropertyByName_Ref(person, "name", &nameValueRet);
    if (status != ANI_OK) {
        // handle error and return
    }
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
    ani_status status = env->String_NewUTF8(name.data(), name.size(), &nameValue);
    if (status != ANI_OK) {
        // handle error and return
    }
    ani_int ageValue = 42;

    status = env->Object_SetFieldByName_Int(person, "age", ageValue);
    if (status != ANI_OK) {
        // handle error and return
    }
    status = env->Object_SetFieldByName_Ref(person, "name", nameValue);
    if (status != ANI_OK) {
        // handle error and return
    }

    ani_int ageValueRet = 0;
    ani_ref nameStringRet {};
    status = env->Object_GetFieldByName_Int(person, "age", &ageValueRet);
    if (status != ANI_OK) {
        // handle error and return
    }
    status = env->Object_GetFieldByName_Ref(person, "name", &nameStringRet);
    if (status != ANI_OK) {
        // handle error and return
    }
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
    ani_status status = env->FindClass(className, &cls);
    if (status != ANI_OK) {
        // handle error and return
    }
    status = env->Class_FindMethod(cls, "managedFunc", ":", &managedFunc);
    if (status != ANI_OK) {
        // handle error and return
    }
    std::cout << "Print in Native Func" << std::endl;
    status = env->Object_CallMethod_Void(obj, managedFunc);
    if (status != ANI_OK) {
        // handle error and return
    }
}
```
## 可选方法作为可选参数

ArkTS-Sta不直接支持可选方法，可使用可选函数参数代替。

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
    ani_status status = env->Object_GetFieldByName_Ref(opt, "fn", &fnRef);
    if (status != ANI_OK) {
        // handle error and return
    }

    // Note: functional objects always accept and return boxed primitives
    std::array<ani_ref, 2> args = {createDouble(env, val1), createDouble(env, val2)};
    ani_ref fnReturnVal {};
    status = env->FunctionalObject_Call(static_cast<ani_fn_object>(fnRef), args.size(), args.data(), &fnReturnVal);
    if (status != ANI_OK) {
        // handle error and return
    }

    ani_double result {};
    status = env->Object_CallMethodByName_Double(static_cast<ani_object>(fnReturnVal), "toDouble", ":d", &result);
    if (status != ANI_OK) {
        // handle error and return
    }
    return result;
}
```

## Native指针包装与释放

当ArkTS对象需要关联C++侧对象实例时，可以在ArkTS类中保存一个`long`字段，用于存放native指针。C++侧创建对象后，将指针转换为`ani_long`写入该字段；后续native实例方法再读取该字段，并转换回对应的C++指针使用。

这种方式常用于把C++对象生命周期挂到ArkTS对象上。需要注意，`long`字段只保存指针值，本身不会自动释放native资源；应配合`FinalizationRegistry`或显式释放接口，在ArkTS对象不再使用时清理C++对象。

示例：

```ts
interface Cleaner {
    ptr: long;
    clean(): void
}

class contextCleaner implements Cleaner {
    ptr: long = 0;
    native static cleanContext(ptr: long): void;
    clean(): void {
        contextCleaner.cleanContext(this.ptr)
    }
}

function callback(cleaner: Cleaner): void {
    cleaner.clean()
}

let destroyRegister = new FinalizationRegistry<Cleaner>(callback)

class Contex {
    private nativeContext: long = 0;
    private cleaner: Cleaner = new contextCleaner();

    constructor(context: long) {
        if(this.nativeContext == 0) {
             this.nativeContext = context;
        }

        if(this.cleaner.ptr == 0) {
            this.cleaner.ptr = this.nativeContext;
        }
        this.registerCleaner(this.cleaner)
    }

    // 注册到FinalizationRegistry，ArkTS对象被GC回收后，
    // 回调中调用cleaner.clean()释放C++侧资源。token传this，支持按需注销。
    registerCleaner(myCleaner: Cleaner): void {
        destroyRegister.register(this, this.cleaner, this);
    }
    unregisterCleaner(): void {
        destroyRegister.unregister(this);
    }

    native static create(): Contex;
    native startAbilitySync(): void;
    native getTempDirSync(): string;
}

function main()
{
    let ctx: Contex | null = null
    ctx = Contex.create();

    ctx.startAbilitySync();
    let str = ctx.getTempDirSync();
    console.info("getTempDirSync: " + str + " .");

    // unregister按需使用
    // ctx.unregisterCleaner()

    ctx = null
    // 执行GC后，监听协程调度callback，触发Cleaner.clean()释放native资源
    GC.waitForFinishGC(GC.startGC(GC.Cause.FULL, GC.IN_PLACE_MODE));
    Coroutine.Schedule()

    console.info("end")
}
```

native侧实现：

```cpp
// 与ArkTS侧Contex类对应的C++对象。
class Context {
public:
    std::string getTempDir(){
        return std::string("/usr/tmp");
    }
    void startAbility(){
        std::cout << "start ability" << std::endl;
    }
    ~Context(){
        std::cout << "~Context destroyed" << std::endl;
    }
};

// 读取nativeContext字段，还原为C++指针。
static Context *unwrap(ani_env *env, ani_object object) {
    ani_long context;
    if (ANI_OK != env->Object_GetFieldByName_Long(object, "nativeContext", &context)) {
        return nullptr;
    }
    return reinterpret_cast<Context *>(context);
}

// static native create(): Contex —— 创建C++对象，并将指针包装进ArkTS对象。
static ani_object create(ani_env *env, [[maybe_unused]] ani_class clazz){
    auto nativeContext = new Context();

    static const char *className = "ani_wrap_native_ptr.Contex";
    ani_class cls;
    ani_status status = env->FindClass(className, &cls);
    if (status != ANI_OK) {
        // handle error and return
    }

    // 构造函数Contex(context: long)会将指针写入nativeContext字段。
    ani_method ctor;
    status = env->Class_FindMethod(cls, "<ctor>", "l:", &ctor);
    if (status != ANI_OK) {
        // handle error and return
    }

    ani_object contextObject;
    status = env->Object_New(cls, ctor, &contextObject, reinterpret_cast<ani_long>(nativeContext));
    if (status != ANI_OK) {
        // handle error and return
    }
    return contextObject;
}

// 实例方法：读回指针，调用C++对象的方法。
static void startAbilitySync([[maybe_unused]] ani_env *env, ani_object object) {
    auto context = unwrap(env, object);
    if (context != nullptr) {
        context->startAbility();
    }
}

static ani_string getTempDirSync([[maybe_unused]] ani_env *env, ani_object object) {
    auto context = unwrap(env, object);
    auto dir = context->getTempDir();
    ani_string ret;
    ani_status status = env->String_NewUTF8(dir.c_str(), dir.size(), &ret);
    if (status != ANI_OK) {
        // handle error and return
    }
    return ret;
}

// contextCleaner的静态native方法：由FinalizationRegistry回调触发，释放C++对象。
static void cleanContext([[maybe_unused]] ani_env *env, [[maybe_unused]] ani_object object, ani_long ptr) {
    delete reinterpret_cast<Context *>(ptr);
}
```

