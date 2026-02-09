# Annotations

Annotations用于为程序元素（类、函数、字段等）添加元数据，配合编译器或运行时框架完成校验、代码生成和行为扩展等能力。

## Target

`@Target`是定义在`std.annotations`包中的标准元注解，用于说明“此注解可应用于源码中的哪些位置”，通过参数`targets: AnnotationTargets[]`指定。

`AnnotationTargets`枚举定义如下：

- `CLASS`：类声明。
- `ENUMERATION`：枚举声明。
- `FUNCTION`：普通函数。
- `FUNCTION_WITH_RECEIVER`：带接收者的函数（扩展函数等）。
- `INTERFACE`：接口声明。
- `NAMESPACE`：命名空间。
- `TYPE_ALIAS`：类型别名。
- `VARIABLE`：顶层变量或属性。
- `CLASS_FIELD`：类字段。
- `CLASS_METHOD`：类方法。
- `CLASS_GETTER`：类的getter。
- `CLASS_SETTER`：类的setter。
- `INTERFACE_PROPERTY`：接口属性。
- `INTERFACE_METHOD`：接口方法。
- `INTERFACE_GETTER`：接口的getter。
- `INTERFACE_SETTER`：接口的setter。
- `LAMBDA`：Lambda 表达式。
- `PARAMETER`：形参。
- `STRUCT`：结构体。
- `TYPE`：类型使用位置（如类型参数等）。

### 参数说明

`@Target`只有一个参数：

| 参数名  | 类型                  | 必填 | 说明                 |
| ------- | --------------------- | ---- | -------------------- |
| targets | `AnnotationTargets[]` | 是   | 允许使用的目标集合。 |

规则简述：

- 只能标注在注解声明上；用于其他位置会产生编译期错误。
- 声明了`@Target`的注解，只能在`targets`指定的位置使用，否则编译期错误；未声明`@Target`的注解，使用位置不受限制。
- 同一个`@Target`中，枚举常量不能重复出现，否则编译期错误。

### 示例

**短写形式（直接传入数组）**

```ts
// 只允许用于普通函数和类方法
@Target([AnnotationTargets.FUNCTION, AnnotationTargets.CLASS_METHOD])
@interface SpecialCall {/* some fields */}
```

**长写形式（传入对象字面量）**

```ts
// 只允许用于参数
@Target({targets: [AnnotationTargets.PARAMETER]})
@interface SpecialParameter {/* some fields */}
```

在上述示例中，`SpecialCall`只能用于函数和类方法，`SpecialParameter`只能用于参数；省略`@Target`时，注解使用位置不受限制。
 
## Retention
 
`@Retention`是定义在`std.annotations`包中的标准元注解，用于指定注解在编译与运行过程中的保留时机，通过参数`policy: string`控制。

`policy`只允许以下三个字符串常量：

- `"SOURCE"`：只在编译期存在，编译后丢弃，不写入字节码，运行时不可见。
- `"BYTECODE"`：写入字节码文件，但运行时丢弃，运行时不可见。
- `"RUNTIME"`：写入字节码文件，并在运行时保留，可通过反射等方式访问。

如果注解声明上未使用`@Retention`，默认策略为`"BYTECODE"`；使用上述三种以外的字符串字面量，会产生编译期错误。

### 参数说明

`@Retention`只有一个参数：

| 参数名 | 类型     | 必填 | 说明                      |
| ------ | -------- | ---- | ------------------------- |
| policy | `string` | 是   | 注解保留策略字符串常量。 |

### 示例

**标准用法：运行时可见的注解**

```ts
@Target([
  AnnotationTargets.CLASS,
  AnnotationTargets.CLASS_METHOD
])
@Retention({ policy: "RUNTIME" })
@interface Audit {
  action: string;
}

@Audit({ action: "user_service" })
class UserService {

  @Audit({ action: "create_user" })
  createUser() {
  }
}
```

`@Audit`使用`"RUNTIME"`策略，适合在运行时通过反射读取元数据（如权限校验、审计日志等）。

**短写形式的用法（单参数注解的简写）**

由于`@Retention`只有一个参数`policy`，可以使用短写形式，直接传入字符串字面量：

```ts
@Retention("SOURCE")
@interface Author {
  name: string;
} // 该注解使用 "SOURCE" 策略
```

**仅编译期使用的校验注解**

```ts
@Target([ AnnotationTargets.CLASS_FIELD ])
@Retention({ policy: "SOURCE" })
@interface Range {
  min: number;
  max: number;
}

class Config {
  @Range({ min: 1, max: 10 })
  retryTimes: number;
}
```

`@Range`使用`"SOURCE"`策略，只在编译期参与静态检查，不会增加运行时开销。

