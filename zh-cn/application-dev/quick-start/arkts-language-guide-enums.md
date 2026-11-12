---
kits: ["ArkTS Kit / 方舟编程语言"]
description: "介绍ArkTS枚举类型的声明与使用，涵盖数值与字符串枚举、带关联值的枚举、const enum及关联值与枚举成员的映射等特性。"
keywords: [ArkTS, 枚举, enum, 数值枚举, 字符串枚举, const enum]
doctype: guide
status: active
---

# 枚举
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @jokerxd-liu-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

枚举（Enum）是一种用户自定义类型，包含一组有限的、命名的常量值。枚举的主要用途是将魔术数字或字符串替换为有意义的名字，使代码更清晰可读、更易维护。

## 枚举的定义和使用

ArkTS支持数值枚举和字符串枚举两种形式。

### 简单枚举的定义

枚举通过`enum`关键字定义，例如：

<!-- @[basic_enum_declaration](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Enums.ets) -->

``` TypeScript
// 枚举定义
enum Direction {
  Up,
  Down,
  Left,
  Right
}
let direction: Direction = Direction.Up;
```

这里定义了枚举类型`Direction`，它包含四个枚举成员`Up`、`Down`、`Left`和`Right`。

这些枚举成员通过限定名访问，如`Direction.Up`。

枚举的使用方式如下：

<!-- @[enum_as_function_parameter](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Enums.ets) -->

``` TypeScript
// 枚举作为函数参数
function declarationMove(direction: Direction): void {
  switch (direction) {
    case Direction.Up:
      console.info('向上');
      break;
    case Direction.Down:
      console.info('向下');
      break;
    case Direction.Left:
      console.info('向左');
      break;
    case Direction.Right:
      console.info('向右');
      break;
  }
}

declarationMove(Direction.Up);  // 向上
```

## 带关联值的枚举

枚举成员可显式指定数值或字符串作为关联值，用于序列化、持久化或与外部接口对接。

### 数值枚举

未显式赋值的成员会自动获得递增的数值，从0开始或从上一个显式值继续递增。

<!-- @[auto_increment_numeric_enum](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Enums.ets) -->

``` TypeScript
// 数值枚举自动递增
enum AutoNumberEnum {
  First,    // 0（自动）
  Second,   // 1（自动）
  Third,    // 2（自动）
  Custom = 10,
  Fourth,   // 11（从Custom继续）
  Fifth     // 12
}
```

### 字符串枚举

字符串枚举必须对每一个枚举成员显式指定关联值。相比数值枚举，字符串枚举的成员值以可读的字符串表示，适用于日志输出、数据序列化等场景。

<!-- @[enum_auto_increment_rules](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Enums.ets) -->

``` TypeScript
enum AutoStringEnum {
  A = 'A',
  B = 'B',
  C = 'C'
}
```

### 关联值类型约束

在同一枚举中，所有枚举成员的关联值类型必须保持一致，混用字符串与数值会导致编译错误。

<!-- @[enum_mixed_type_error](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Enums.ts) -->

``` TypeScript
enum Mixed {
  No = 0,
  Yes = 'YES'  // 编译错误：关联值类型不一致
}
```

### 关联值与枚举成员的映射

数值枚举支持通过关联值获取枚举成员的名称，而字符串枚举不支持这种使用方式。

<!-- @[enum_bidirectional_mapping](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Enums.ets) -->

``` TypeScript
enum BiUserRole {
  Admin = 100,
  Moderator = 200,
  User = 300
}

let biRole: BiUserRole = BiUserRole.Admin;     // 100
let biRoleName: string = BiUserRole[100];      // 'Admin'

function getBiRoleName(roleId: number): string | undefined {
  return BiUserRole[roleId];
}

console.info(`${getBiRoleName(100)}`);  // 'Admin'
console.info(`${getBiRoleName(200)}`);  // 'Moderator'
```

### 枚举成员作为字面量类型使用

枚举成员是一种字面量类型，可用于将变量或参数的取值限定为某个具体的枚举成员。

<!-- @[ts_enum_member_types](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Enums.ts) -->

``` TypeScript
// 枚举成员是唯一类型
let up: Direction.Up = Direction.Up;  // Direction.Up类型
let down: Direction.Down = Direction.Down;

// 不同成员不能互换
up = down;  // 编译错误：类型不匹配

// 枚举值作为联合类型
type HorizontalDirection = Direction.Left | Direction.Right;
type VerticalDirection = Direction.Up | Direction.Down;

function moveHorizontal(dir: HorizontalDirection): void {
  console.info(`水平移动: ${dir}`);
}

moveHorizontal(Direction.Left);
moveHorizontal(Direction.Up);  // 编译错误：类型不匹配
```

### 使用枚举替代魔术字符串

使用枚举替代魔术字符串/数值，提升代码可读性和可维护性。

<!-- @[replace_magic_strings_numbers](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Enums.ets) -->

``` TypeScript
// 反例：使用魔术字符串
function getStatusLabel(status: string): string {
  if (status === 'pending') {
    return '待处理';
  } else if (status === 'active') {
    return '激活';
  } else if (status === 'completed') {
    return '已完成';
  }
  return '未知';
}

// 推荐：使用枚举
enum OrderStatus {
  Pending = 'pending',
  Active = 'active',
  Completed = 'completed'
}

function getStatusLabelEnum(status: OrderStatus): string {
  switch (status) {
    case OrderStatus.Pending:
      return '待处理';
    case OrderStatus.Active:
      return '激活';
    case OrderStatus.Completed:
      return '已完成';
    default:
      return '未知';
  }
}

// 反例：使用魔术数值
function getErrorCode(code: number): string {
  if (code === 404) {
    return 'Not Found';
  } else if (code === 401) {
    return 'Unauthorized';
  }
  return 'Unknown';
}

// 推荐：使用枚举
enum HttpErrorCode {
  NotFound = 404,
  Unauthorized = 401
}

function getErrorCodeEnum(code: HttpErrorCode): string {
  switch (code) {
    case HttpErrorCode.NotFound:
      return 'Not Found';
    case HttpErrorCode.Unauthorized:
      return 'Unauthorized';
    default:
      return 'Unknown';
  }
}
```

## const enum

`const enum`在编译时内联成员值，不生成运行时枚举对象。ArkTS支持`const enum`。但需注意：跨项目共享时（通过`.d.ts`文件）存在版本依赖风险，`const enum`的成员值在编译时被内联到消费方的代码中，若源定义变更，消费方需重新编译才能获取新值。推荐项目内部使用`const enum`，跨项目共享时使用普通枚举。

<!-- @[const_enum_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Enums.ets) -->

``` TypeScript
const enum CeConstDirection {
  Up,
  Down
}

let cedDir: CeConstDirection = CeConstDirection.Up;
console.info(`${cedDir}`); // 0
```

使用普通枚举替代`const enum`，可避免跨项目陷阱：

<!-- @[const_enum_alternative](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Enums.ets) -->

``` TypeScript
enum CeDirection {
  Up = 0,
  Down = 1
}

let ceD: CeDirection = CeDirection.Up;
console.info(`${ceD}`);  // 0
```
