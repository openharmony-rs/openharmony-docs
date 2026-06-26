# 反射与错误处理 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: RuntimeCore-->
<!--Owner: @lijin1039-->
<!--Designer: @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @HelloCrease-->

ArkTS-Sta运行时提供完整的反射系统和错误处理机制，反射方面，ArkTS-Sta通过Class.from\<T\>()获取运行时类型信息；错误处理方面，ArkTS-Sta定义了以Error为基类的完整ETS Error类型层级。

## 反射机制

ArkTS-Sta提供Class.from反射、内建函数、ReflectMethod/ReflectField、instanceof/checkcast运算符、动态代理和Smart Casts等反射能力。

### Class.from\<T\>()反射

标准库提供伪泛型静态方法`Class.from<T>()`用于获取运行时类型信息：

```typescript
let type_of_int: Class = Class.from<int>()
let type_of_string: Class = Class.from<string>()
let type_of_Object: Class = Class.from<Object>()

class UserClass {}
let type_of_user_class: Class = Class.from<UserClass>()

interface SomeInterface {}
let type_of_interface: Class = Class.from<SomeInterface>()
```

> **说明：**
>
> 与ArkTS-Dyn的`typeof`运算符不同，ArkTS-Sta的`Class.from<T>()`返回完整的Class对象，包含类名、方法列表、字段列表等详细类型信息。

### 类型擦除对反射的影响

当前编译器和运行时使用**类型擦除**，`Class.from<T>()`返回T的有效类型而非T本身：

```typescript
let type_of_array1: Class = Class.from<int[]>()       // Class值对应Array<>
let type_of_array2: Class = Class.from<Array<number>>() // 相同的Class值
```

> **注意：**
>
> 类型擦除导致`instanceof`对泛型类型参数检查受限：
> - `arr instanceof Array<number>` 无效（运行时擦除为`Array<Object>`）。
> - `Class.from<Array<int>>()` 与 `Class.from<Array<string>>()` 返回相同的Class值。

### Class内建函数

ETS Class对象提供以下反射内建函数：

| 内建函数 | 功能 | 示例 |
| -------- | -------- | -------- |
| `getNameInternal` | 获取类名 | `cls.getNameInternal()` |
| `ofObject` | 从对象实例获取其Class | `Class.ofObject(obj)` |
| `isSubtypeOf` | 子类型检查 | `cls.isSubtypeOf(otherCls)` |
| `getInstanceMethodsInternal` | 获取实例方法列表 | `cls.getInstanceMethodsInternal()` |
| `getStaticMethodsInternal` | 获取静态方法列表 | `cls.getStaticMethodsInternal()` |
| `getConstructorsInternal` | 获取构造器列表 | `cls.getConstructorsInternal()` |
| `getInstanceFieldsInternal` | 获取实例字段列表 | `cls.getInstanceFieldsInternal()` |
| `getStaticFieldsInternal` | 获取静态字段列表 | `cls.getStaticFieldsInternal()` |
| `getInterfaces` | 获取实现的接口列表 | `cls.getInterfaces()` |
| `isEnum` / `IsInterface` / `IsFinal` / `IsAbstract` / `IsPrimitive` | 类型特征检查 | `cls.isInterface()` |

### ReflectMethod与ReflectField

**EtsReflectMethod**

`EtsReflectMethod`是托管包装类，将native `Method*`指针以`EtsLong`形式存储：

```typescript
// 使用示例
let methods: ReflectMethod[] = cls.getInstanceMethodsInternal()
for (let method of methods) {
  console.info(method.getName())        // 方法名
  console.info(method.getReturnType())  // 返回类型
  method.invoke(obj, args)              // 调用方法
}
```

**EtsReflectField**

`EtsReflectField`类似地将native `Field*`指针以`EtsLong`形式存储：

```typescript
// 使用示例
let fields: ReflectField[] = cls.getInstanceFieldsInternal()
for (let field of fields) {
  console.info(field.getName())   // 字段名
  console.info(field.getType())   // 字段类型
  field.get(obj)                  // 获取字段值
  field.set(obj, newValue)        // 设置字段值
}
```

### instanceof运算符

**规格定义**

`instanceof`表达式用于运行时类型检查：

```typescript
if (obj instanceof MyClass) {
  // obj被Smart Cast为MyClass类型
}
```

**IsAssignableFrom逻辑 (RefIsAssignableToImpl)**：

| 检查步骤 | 条件 | 结果 |
| -------- | -------- | -------- |
| 1. 身份检查 | source == target | true |
| 2. Any检查 | target == ANY | true |
| 3. Never检查 | source == NEVER | true |
| 4. Object检查 | target == OBJECT | true（所有引用类型都是Object子类型） |
| 5. 接口检查 | target是接口 | 检查source的ITable是否包含target |
| 6. 数组检查 | 两者都是数组 | 递归检查元素类型的可赋值性 |
| 7. 超类链 | 沿super_class_链向上查找 | 找到匹配则true，否则false |

### checkcast运算符

`checkcast`与`instanceof`共享底层逻辑，但行为不同：
- `instanceof`返回boolean结果
- `checkcast`失败时抛出`ClassCastError`

```typescript
let obj: Object = someValue
let myObj: MyClass = obj as MyClass  // checkcast，失败时抛ClassCastError

// 等价于
if (obj instanceof MyClass) {
  let myObj: MyClass = obj  // Smart Cast
} else {
  throw new ClassCastError()
}
```

### 动态代理

`reflect.Proxy.create(linker, ifaces, handler)` 支持动态代理创建：

```typescript
let handler: reflect.InvocationHandler = {
  invoke(target: Object, method: ReflectMethod, args: Object[]): Object {
    // 自定义代理逻辑
    return method.invoke(target, args)
  }
}

let proxy: Object = reflect.Proxy.create(classLinker, [SomeInterface], handler)
```

### Smart Casts

编译器通过数据流分析实现**智能类型转换**：

```typescript
let obj: Object = someValue
if (obj instanceof MyClass) {
  // 此处obj被Smart Cast为MyClass类型，无需再次转换
  obj.myClassMethod()  // 直接调用，编译器保证类型安全
}
```

**Smart Cast限制**：

- 不应用于全局变量和类字段（难以追踪值变化）。
- Lambda中捕获和修改的变量不应用Smart Cast。
- 循环和try-catch块中的数据流检查尚未完全实现。

## 错误处理

ArkTS-Sta定义了ETS Error类型体系，通过描述符驱动的异常抛出机制处理运行时错误和链接错误。

### Error类型

ArkTS-Sta运行时定义了完整的ETS Error类型层级，与ArkTS-Dyn的ECMAScript Error层级不同。以Error为基类，派生出运行时错误（NullPointerError、RangeError、ArithmeticError、OutOfMemoryError、StackOverflowError、ClassCastError等）和链接错误（LinkerError及其子类LinkerUnresolvedClassError、LinkerMethodConflictError、LinkerIncompatibleClassChangeError等）。

> **说明：**
>
> ArkTS-Sta的Error命名与ArkTS-Dyn不同。例如：
> - ArkTS-Sta使用`NullPointerError`，ArkTS-Dyn使用`TypeError`（null访问场景）。
> - ArkTS-Sta使用`ClassCastError`，ArkTS-Dyn无对应错误类型。
> - ArkTS-Sta使用`ArithmeticError`，ArkTS-Dyn在非整数场景可能不抛异常。

### throw与try

- `throw`语句创建并抛出新错误。
- `try`语句处理错误（try-catch-finally）。
- 部分错误不可恢复（如OutOfMemoryError、StackOverflowError）。

```typescript
try {
  let result: int = a / b
} catch (e: ArithmeticError) {
  console.info("除零错误: " + e.message)
} catch (e: RangeError) {
  console.info("越界错误: " + e.message)
} catch (e: Error) {
  console.info("其他错误: " + e.message)
}
```

### 异常抛出机制

运行时异常机制是**描述符驱动、语言无关**的：

| ETS Error | 运行时描述符 | 触发场景 |
| -------- | -------- | -------- |
| ArithmeticError | Lstd/core/ArithmeticError | 整数除零、取余零 |
| NullPointerError | Lstd/core/NullPointerError | 空指针访问 |
| RangeError | Lstd/core/RangeError | 数组索引越界 |
| ClassCastError | Lstd/core/ClassCastError | 类型转换失败 |
| OutOfMemoryError | Lstd/core/OutOfMemoryError | 内存不足 |
| StackOverflowError | Lstd/core/StackOverflowError | 栈溢出 |
| LinkerUnresolvedClassError | Lstd/core/LinkerUnresolvedClassError | 类找不到 |
| LinkerMethodConflictError | Lstd/core/LinkerMethodConflictError | 方法冲突 |

**Throw流程**：

1. Throw*函数（如ThrowNullPointerError）构造描述符 `Lstd/core/NullPointerError`。
2. 语言扩展决定使用哪个描述符（ETS使用`Lstd/core/*Error`，Core使用`Lpanda/*Exception`）。
3. 从ClassLinker查找Error类，创建Error实例，设置stack trace。
4. 设置当前线程的`exception_`字段，异常传播到catch块。

### 常见运行时错误对照表

| 错误 (ETS) | 触发场景 | 实现位置 |
| -------- | -------- | -------- |
| ArithmeticError | `let x: int = 10 / 0` | entrypoints, interpreter |
| RangeError | `arr[100]` 当arr.length=5 | entrypoints, interpreter |
| NullPointerError | `obj.method()` 当obj=null | interpreter, compiled code |
| OutOfMemoryError | 创建超大数组 | HeapManager |
| StackOverflowError | 递归调用无终止 | SignalHandler |
| ClassCastError | `obj as MyClass` 失败 | CheckCastEntrypoint |
| NegativeArraySizeError | `new int[-1]` | array creation |
| ArrayStoreError | FixedArray存类型不匹配 | array store |
| LinkerUnresolvedClassError | import的类不存在 | ClassLinker |
| LinkerMethodConflictError | 方法签名冲突 | ClassLinker |
| VerifyError | 二进制文件验证失败 | Verifier |

### StackOverflowError特殊处理

StackOverflowError采用**信号机制**检测：

1. 线程栈底部设置Guard Page（不可访问页）。
2. 函数调用超出栈空间 → 触发SIGSEGV信号。
3. SignalHandler检测到是栈溢出而非非法内存访问。
4. 抛出**预先分配**的StackOverflowError。
5. 使用ReservedStack空间处理异常。

> **注意：**
>
> StackOverflowError和OutOfMemoryError在运行时启动时预先创建，避免在内存不足或栈溢出时再次触发同类错误导致无限递归。在catch块中处理这些错误时应避免创建新对象。

### OutOfMemoryError特殊处理

1. 对象分配失败时，HeapManager最多尝试4次GC + 重新分配。
2. 每次GC前增大回收力度（Young → Mixed → Full）。
3. 4次尝试后仍然失败 → 抛出预先分配的OutOfMemoryError。

## 反射与错误处理常见问题

以下是反射和错误处理中的常见问题及解决方向。

### instanceof对泛型类型检查无效

**问题现象**

```typescript
let arr: Object = new Array<int>()
if (arr instanceof Array<number>) {
  // 期望进入此分支，但实际不会进入
}
```

**可能原因**

当前实现使用类型擦除，`Array<int>`和`Array<number>`在运行时擦除为相同的`Array<Object>`类型。`instanceof`无法区分泛型参数。

**规避方案**

使用`Class.from<T>()`获取数组的Class，检查元素类型：

```typescript
let arr: Object = new Array<int>()
let arrClass: Class = Class.ofObject(arr)
// 注意：类型擦除下，arrClass仅对应Array<>，无法获取元素类型信息
```

### Class.from返回有效类型而非T本身

**问题现象**

```typescript
let cls: Class = Class.from<int[]>()
let cls2: Class = Class.from<Array<number>>()
// cls和cls2指向相同的Class对象（类型擦除后）
```

**可能原因**

类型擦除导致泛型参数信息丢失。

**规避方案**

如果需要区分泛型类型，在编译时通过不同逻辑路径处理，不依赖运行时Class.from的精确类型信息。

### checkcast抛出ClassCastError而非返回null

**问题现象**

```typescript
let obj: Object = "hello"
let num: int = obj as int  // 抛出ClassCastError，而非返回null或0
```

**可能原因**

ArkTS-Sta的`as`运算符（checkcast）在类型转换失败时抛出ClassCastError，这与ArkTS-Dyn的行为不同。

**规避方案**

使用instanceof先检查类型，再进行转换：

```typescript
let obj: Object = someValue
if (obj instanceof int) {
  let num: int = obj as int  // 安全转换
} else {
  // 处理类型不匹配的情况
}
```

### 异步函数中的异常未被捕获

**问题现象**

async函数内部抛出异常，但在外部try-catch中无法捕获。

**可能原因**

与ArkTS-Dyn相同，async函数内部的异常会变成unhandledRejection，表现为异常未抛出。

**解决措施**

1. 在async函数内部针对可能发生异常的代码块添加try-catch逻辑。
2. 使用errorManager.on()捕获unhandledRejection事件。

```typescript
async function riskyOperation(): Promise<int> {
  try {
    // 可能抛出异常的操作
    return someComputation()
  } catch (e: Error) {
    console.info("捕获异常: " + e.message)
    return 0
  }
}
```

### NullPointerError与null检查

**问题现象**

访问null对象的字段或方法时抛出NullPointerError。

**可能原因**

ArkTS-Sta对null访问采用严格的异常抛出机制，而非返回undefined。

**规避方案**

优先使用undefined而非null：

```typescript
// 不推荐
let obj: MyClass | null = null
if (obj != null) {
  obj.method()
}

// 推荐
let obj: MyClass | undefined = undefined
if (obj != undefined) {
  obj.method()
}
```