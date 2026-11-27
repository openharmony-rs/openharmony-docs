---
kits: ["ArkTS Kit / 方舟编程语言"]
description: "介绍ArkTS的内置类型与自定义类型，涵盖类型别名、联合类型、可空类型与空安全、工具类型、子类型关系、类型守卫、类型断言及类型安全的使用。"
keywords: [ArkTS, 类型系统, 内置类型, 类型别名, 联合类型, 可空类型, 类型守卫, 类型断言, 类型安全]
doctype: guide
status: active
---

# 类型系统
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @jokerxd-liu-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

类型约束了变量、参数和返回值的取值范围与可执行的操作。ArkTS在TypeScript类型系统的基础上强化了静态检查与空安全。本章介绍ArkTS的内置类型与自定义类型、值类型与引用类型的差异、工具类型、子类型关系、类型安全的价值，以及类型守卫与类型断言。

## 内置类型

内置类型是语言预先定义、无需导入即可使用的类型。ArkTS的内置类型如下：

| 类型 | 说明 |
| --- | --- |
| `number` | 数值，整数与浮点数统一表示 |
| `boolean` | 逻辑值，`true`或`false` |
| `string` | 字符串 |
| `bigint` | 任意精度整数 |
| `void` | 函数无返回值 |
| `null` / `undefined` | 空值 / 未定义值 |
| 字面量类型 | 将特定字面量值本身作为类型 |
| `object` / `Object` | 非原始类型 / 所有非空类型的根类型 |
| `never` | 永不存在的值，如总是抛出异常的函数的返回类型 |

### number、boolean、string

`number`表示IEEE 754双精度浮点数（64位），没有独立的整数类型，支持十进制、十六进制、二进制和八进制字面量。`boolean`表示逻辑值，由比较运算和逻辑运算产生。为避免JavaScript的类型混淆问题，ArkTS禁止在赋值、参数传递等位置发生`boolean`与其他类型的隐式转换；模板字面量插值（如`${true}`）将布尔值转为字符串输出，不属于此处所说的隐式转换。条件判断时应直接使用布尔表达式，不要将布尔值与其他类型混用。`string`表示字符串，详见[字符串](arkts-language-guide-strings.md)。

<!-- @[builtin_primitive_types](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
// number：整数与浮点数统一表示
let age: number = 25;
let price: number = 9.99;
let hex: number = 0xFF; // 十六进制字面量

// boolean：逻辑值
let enabled: boolean = true;

// string：字符串
let appName: string = 'ArkTS';
```

### bigint

`bigint`类型表示任意精度的整数，用`n`后缀标记字面量，适合超大整数运算：`bigValue`保存超大整数无精度损失，`nextValue`进行加法运算结果精确。`bigint`不能和`number`直接混合运算，需要通过`BigInt()`显式转换。该类型只支持整数运算，不支持小数。

<!-- @[bigint_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
let bigValue: bigint = 999999999999999999999999999999999999n;
console.info(`${bigValue.toString()}`);

let nextValue: bigint = bigValue + 1n;
console.info(`${nextValue.toString()}`);
```

<!-- @[bigint_conversion](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
let bigintCount: number = 10;
let preciseCount: bigint = BigInt(bigintCount);
let total: bigint = preciseCount + 20n;
```

需要注意的是，某些特定的API（如`Date`相关方法）或注解字段可能不支持`bigint`，使用前应确认对应API文档的类型约束；大整数场景应优先使用`bigint`以避免`number`的精度损失。

### void

`void`表示函数无返回值，用于只执行操作、不返回结果的函数。`void`与`undefined`不同：前者描述函数返回值类型，后者表示值未定义。

<!-- @[void_type_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
function log(message: string): void {
  console.info(`${message}`);
}
```

### null与undefined

`null`表示有意赋予的空值，`undefined`表示变量未赋值或属性不存在，两者语义不同，需显式区分。建议优先使用`undefined`表示值不存在，仅在明确需要表达空值语义时使用`null`。ArkTS默认开启空安全，`null`和`undefined`不能赋给非可空类型（`let name: string = null`是编译错误）。访问可空值前需通过判空检查、可选链（`?.`）或空值合并（`??`）处理，详见[基本运算符](arkts-language-guide-basic-operators.md)。

<!-- @[null_undefined_types_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
// null：明确表示空值
let nickname: string | null = null;

// undefined：未定义值，可选属性的隐含类型为T | undefined
interface NullableUserProfile {
  name: string;
  email?: string;
}

let nullableUser: NullableUserProfile = { name: 'Alice' };
```

<!-- @[null_undefined_types](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
// null：有意的空值
let empty: null = null;
let nullUndefData: string | null = null;

// undefined：未定义值
let missing: undefined = undefined;
let optional: string | undefined = undefined;

// null与undefined区别
let nickname: string | null = null;     // 明确表示没有昵称
let title: string | undefined;          // 可能未提供
```

可空类型（`T | null`/`T | undefined`）与可选属性是表达“值可能不存在”的两种方式：`?`是属性声明时的修饰符（`name?: string`），而可空类型是显式的联合类型标注（`name: string | null`）。

### 字面量类型

字面量类型将值本身作为类型，限制变量只能取特定字面量值，常与联合类型配合，约束取值范围。`const`声明的常量会推断为字面量类型（如`const pi = 3.14`推断为`3.14`）。

<!-- @[literal_type_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
type TaskState = 'pending' | 'running' | 'done';

let state: TaskState = 'pending';
// state = 'finished'; // 编译错误：'finished'不是TaskState的成员

// const声明的常量推断为字面量类型
const pi = 3.14; // 推断为字面量类型 3.14
let piValue: number = pi; // 字面量类型可赋给 number
```

### object与Object

`object`表示非原始类型，包括对象、数组、类实例等引用类型。`Object`是所有非空类型的根类型，任何非`null`、`undefined`的值都可赋给`Object`类型的变量。通过`object`或`Object`类型的变量只能访问所有类型共有的成员，访问具体成员前需先收窄或断言。此外，对象字面量不能直接初始化`Object`或`object`类型的变量，必须对应显式声明的类或接口，详见[从TypeScript到ArkTS的适配规则](typescript-to-arkts-migration-guide.md#需要显式标注对象字面量的类型)。

<!-- @[object_object_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
interface Point {
  x: number;
  y: number;
}

// object：非原始类型
let point: Point = { x: 1, y: 2 };
let ref: object = point;

// Object：所有非空类型的根类型
let boxed: Object = 'hello';
let boxedObj: Object = point;

// Object类型的值访问具体成员前，需要先收窄
if (typeof boxed === 'string') {
  console.info(`${boxed.length}`); // 5
}
```

### never

`never`类型表示永不存在的值，常作为总是抛出异常或无限循环的函数的返回类型。

<!-- @[never_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
function fail(message: string): never {
  throw new Error(message);
}

function assertNever(value: never): never {
  throw new Error(`Unexpected value: ${value}`);
}

interface NevCircle {
  kind: 'circle';
  radius: number;
}

interface NevSquare {
  kind: 'square';
  sideLength: number;
}

type NevShape = NevCircle | NevSquare;

function nevShapeArea(shape: NevShape): number {
  switch (shape.kind) {
    case 'circle':
      return Math.PI * shape.radius * shape.radius;
    case 'square':
      return shape.sideLength * shape.sideLength;
    default:
      // 若联合新增成员未在case覆盖，此处编译报错
      const _check: never = shape;
      return _check;
  }
}
```

`never`类型常用于两类场景：异常函数总是抛出异常永不返回，以及穷尽性检查——在`switch`的`default`分支中将判别值赋给`never`类型变量（如`const _check: never = value;`，也可将判别值传给`assertNever`这类参数类型为`never`的函数）。当`case`未覆盖联合类型的全部成员时，判别值无法赋给`never`，编译器会报错，从而确保`switch`覆盖所有成员。

数组（`T[]`）作为内置引用类型，其声明、遍历与常用操作详见[集合](arkts-language-guide-collection-types.md)。

## 自定义类型

通过组合内置类型或声明新类型，可以构建满足业务建模需求的自定义类型。类型别名（`type`）可以为任意类型起一个新名字，常与联合类型、函数类型配合使用。类、接口、枚举等有专门章节详细介绍，此处仅给出简单示例。

### 类型别名

类型别名使用`type`关键字为已有类型起一个新名字，不创建新类型。常用于为联合类型、函数类型等复杂类型提供语义化的名称，也可为原始类型起更具业务含义的名字。

<!-- @[type_alias_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
// 为原始类型起别名，增强语义
type AccountId = number;
let accountId: AccountId = 1001;

// 为字面量联合类型起别名，约束取值范围
type SortOrder = 'asc' | 'desc';
let order: SortOrder = 'asc';

console.info(`${accountId}`);  // 1001
console.info(`${order}`);      // 'asc'
```

### 联合类型

联合类型表示一个值可以是多种类型之一，用竖线（`|`）分隔。联合类型的值只能直接访问所有成员共有的成员，访问特定类型的成员需先通过类型守卫收窄（详见[类型守卫](#类型守卫)）。可空类型（`T | null`）和可选属性（`prop?: T`，等价于`T | undefined`）是联合类型的常见应用。

<!-- @[union_type_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
type ID = string | number;

let userId: ID = 'A-001';
userId = 100; // 也可以是number

function printId(id: ID): void {
  if (typeof id === 'string') {
    console.info(`${id.toUpperCase()}`); // string特有成员
  } else {
    console.info(`${id.toFixed(0)}`);    // number特有成员
  }
}
```

### 函数类型

函数类型使用`(参数列表) => 返回值类型`的形式描述函数的签名，可将函数赋值给变量、作为参数传递。详见[函数](arkts-language-guide-functions.md)。

<!-- @[function_type_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
type Comparator = (a: number, b: number) => number;

let ascending: Comparator = (a: number, b: number): number => {
  return a - b;
};

console.info(`${ascending(3, 1)}`); // 2
```

### 枚举类型

枚举类型为一组命名的常量值定义类型，便于语义化表达固定状态。

<!-- @[enum_type_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
enum MyColor {
  Red,
  Green,
  Blue
}

let favorite: MyColor = MyColor.Blue;
```

详见[枚举](arkts-language-guide-enums.md)。

### 接口

接口定义对象的结构契约，描述属性名、类型和可选性。

<!-- @[interface_type_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
interface MyPosition {
  x: number;
  y: number;
}

let origin: MyPosition = { x: 0, y: 0 };
```

详见[接口](arkts-language-guide-interfaces.md)。

### 类

类同时定义数据结构与行为，是唯一可以通过`new`创建实例的自定义类型。

<!-- @[class_type_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
class MyRectangle {
  public width: number;
  public height: number;

  constructor(width: number, height: number) {
    this.width = width;
    this.height = height;
  }

  public getArea(): number {
    return this.width * this.height;
  }
}

let rect: MyRectangle = new MyRectangle(3, 4);
console.info(`${rect.getArea()}`); // 12
```

详见[类](arkts-language-guide-classes.md)。

## 值类型与引用类型

按内存分配与访问方式，ArkTS的类型分为两类：值类型（`number`、`boolean`、`string`、`null`、`undefined`等原始类型）直接存储值，赋值时复制值本身；引用类型（对象、数组、类实例、函数等）存储对象的引用，赋值时复制引用，多个变量指向同一个对象。

### 赋值行为的差异

值类型赋值后两个变量相互独立，修改其中一个不影响另一个；引用类型赋值后两个变量共享同一个对象。

<!-- @[value_reference_assignment](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
// 值类型：赋值复制值，两个变量相互独立
let countA: number = 10;
let countB: number = countA;
countB = 20;
console.info(`${countA}`); // 10（不受countB影响）

// 引用类型：赋值复制引用，两个变量指向同一个对象
interface Score {
  value: number;
}

let scoreA: Score = { value: 90 };
let scoreB: Score = scoreA;
scoreB.value = 95;
console.info(`${scoreA.value}`); // 95（scoreA随之改变）
```

### 修改状态对原对象的影响

通过任一引用修改对象的状态，所有指向该对象的引用都能观察到变化，函数传参同样如此。传递引用类型时，函数内修改的是原对象的状态；传递值类型时，函数内只操作副本，不影响外部变量。如需复制对象而非共享引用，需进行浅拷贝或深拷贝，详见[类](arkts-language-guide-classes.md#类的定义)。

<!-- @[value_reference_mutation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
class Task {
  public status: string = 'pending';
}

// 引用类型作为参数：函数内修改原对象的状态
function start(task: Task): void {
  task.status = 'running';
}

let myTask: Task = new Task();
start(myTask);
console.info(`${myTask.status}`); // running（原对象被修改）

// 值类型作为参数：函数内只修改副本
function double(value: number): number {
  value = value * 2; // 仅修改副本
  return value;
}

let count: number = 10;
double(count);
console.info(`${count}`); // 10（不变）
```

## 工具类型

ArkTS支持少量类型层面的工具类型（Utility Types）对已有类型做变换，仅包括`Partial<T>`、`Required<T>`、`Readonly<T>`和`Record<K, V>`，其他工具类型（如`Pick<T, K>`、`Omit<T, K>`）不支持。

### Partial与Required

`Partial<T>`将T的所有属性变为可选，适合表达部分更新的对象结构；`Required<T>`将T的所有属性变为必选。`Partial<T>`的泛型参数T必须是类或接口类型。

<!-- @[partial_required_types](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
interface UserProfile {
  id: number;
  name: string;
  email: string;
}

// Partial<T>：所有属性变为可选
let patch: Partial<UserProfile> = { name: 'Alice' };

interface PageQuery {
  keyword?: string;
  pageSize?: number;
}

// Required<T>：所有属性变为必选
let strictQuery: Required<PageQuery> = { keyword: 'arkts', pageSize: 20 };
```

### Readonly

`Readonly<T>`将T的所有属性变为只读，初始化后不可修改。类的单个只读属性也可用`readonly`修饰符声明。

<!-- @[readonly_type_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
interface AppConfig {
  appId: string;
  version: string;
}

let config: Readonly<AppConfig> = { appId: 'com.example.app', version: '1.0.0' };
// config.version = '1.0.1'; // 编译错误：属性为只读
```

### Record

`Record<K, V>`将键类型K映射到值类型V，键类型`K`只能为`string`或`number`，适合表达键值结构。通过索引访问`Record`对象的值时，结果类型是包含`undefined`的联合类型。`Record`的更多用法详见[集合](arkts-language-guide-collection-types.md)。

<!-- @[record_type_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
interface CityInfo {
  country: string;
  population: number;
}

let cityMap: Record<string, CityInfo> = {
  'Beijing': { country: 'China', population: 21860000 }
};

let info: CityInfo | undefined = cityMap['Beijing']; // 索引访问结果包含undefined
```

此外，交叉类型、条件类型、映射类型、索引访问类型（`T[K]`）等类型操作在ArkTS中均不支持。泛型场景下优先使用显式接口、类或泛型约束表达结构，详见[泛型](arkts-language-guide-generics.md)。

## 子类型

若类型S的任意值都可以安全地赋给类型T的变量，则称S是T的子类型。ArkTS不支持结构化类型（鸭子类型），编译器不通过比较两个类型的结构判定兼容性，类型之间的子类型关系基于显式的继承和`implements`关系。

### 父子类

子类是父类的子类型。子类实例可隐式赋给父类类型变量（向上转型），转型后只能访问父类声明的成员；父类变量赋给子类变量（向下转型）不是类型安全的：在`instanceof`守卫分支内，变量自动收窄为子类型，可直接赋值（见下方示例）；守卫外必须使用`as`断言，并建议先用`instanceof`确认实际类型。

<!-- @[subtype_class_hierarchy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
class Creature {
  public name: string;

  constructor(name: string) {
    this.name = name;
  }

  public speak(): void {
    console.info(`${this.name} makes a sound`);
  }
}

class Hound extends Creature {
  public breed: string;

  constructor(name: string, breed: string) {
    super(name);
    this.breed = breed;
  }

  public bark(): void {
    console.info(`${this.name} barks: Woof!`);
  }
}

// 向上转型：子类实例可隐式赋给父类类型变量
let hound: Hound = new Hound('Buddy', 'Golden Retriever');
let creature: Creature = hound;
creature.speak(); // 'Buddy makes a sound'
// creature.bark(); // 编译错误：父类类型变量不能访问子类特有成员

// 向下转型：需先确认实际类型
if (creature instanceof Hound) {
  let myHound: Hound = creature; // 守卫分支内自动收窄
  myHound.bark(); // 'Buddy barks: Woof!'
}
```

实现类与接口之间同理：声明了`implements`的类实例可隐式赋给接口类型的变量，反之需要断言。

### 函数类型的子类型关系

函数赋给函数类型变量时，需满足函数的子类型规则：源函数的参数个数可以更少但不能更多；参数类型可以是目标参数类型的父类型（参数逆变）；返回值类型必须是目标返回值类型的子类型（返回值协变）。

<!-- @[subtype_function_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
class BaseType {}
class SubType extends BaseType {}

// 目标函数类型：(SubType) => BaseType
type Handler = (input: SubType) => BaseType;

// 参数为父类型（逆变）、返回值为子类型（协变），满足子类型规则
let handler: Handler = (input: BaseType): SubType => {
  return new SubType();
};

// 参数更少的函数可赋给参数更多的函数类型
type BinaryOp = (a: number, b: number) => number;
let doubleFn: BinaryOp = (a: number): number => a * 2;
```

### 联合类型的子类型关系

联合类型的每个成员类型都是该联合类型的子类型，因此`string`和`number`的值都可赋给`string | number`类型的变量；反过来，联合类型不是其成员的子类型，`string | number`类型的值不能赋给`string`类型的变量。

<!-- @[subtype_union_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
type Identifier = string | number;

// string和number都是Identifier的子类型
let id: Identifier = 'A-001';
id = 100;

let displayName: string = 'Alice';
id = displayName;    // OK：string是string | number的子类型
// displayName = id; // 编译错误：string | number不是string的子类型
```

## 类型安全

类型安全在编译期捕获类型错误，减少运行时产生难以排查的问题。编译器拒绝类型不匹配的赋值（如将`string`赋给`number`变量）与类型不匹配的调用，开发者无需等待运行时即可发现错误。

<!-- @[ts_type_mismatch](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Basics.ts) -->

``` TypeScript
let typeCheckAge: number = 25;
typeCheckAge = 'text';  // 编译错误：类型不匹配

function typeCheckAdd(a: number, b: number): number {
  return a + b;
}

typeCheckAdd(1, 2);      // 正确
typeCheckAdd(1, '2');    // 编译错误
```

类型安全能在编译期提前发现错误、避免运行时崩溃，同时提高代码可读性和重构安全性，并支持DevEco Studio的智能提示。

## 类型守卫

类型守卫在运行时检查值的实际类型，并在编译时将联合类型收窄为具体类型。在守卫条件成立的分支内，可以直接访问该类型的特有成员，无需类型断言。相比类型断言，类型守卫执行真实的运行时检查，是更安全的类型收窄方式。

### 控制流推断

编译器沿`if`/`else`、`switch`、循环等控制流分支追踪类型变化，在不同分支内将变量收窄为更具体的类型，分支合并后取联合类型。后文的`typeof`、`instanceof`等类型守卫都建立在这一机制之上。

<!-- @[type_inference_control_flow](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
let tiValue: string | number = 'hello';
if (typeof tiValue === 'string') {
  console.info(tiValue.toUpperCase()); // 此处tiValue收窄为string
} else {
  console.info(`${tiValue}`);          // 此处tiValue收窄为number
}
```

### typeof类型守卫

`typeof`用于检查基础类型，常用于收窄`string`、`number`、`boolean`等原始类型的联合。

<!-- @[typeof_type_guard](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
function typeGuardProcessValue(value: string | number | boolean): void {
  if (typeof value === 'string') {
    // 编译器知道value是string类型
    console.info(`字符串长度: ${value.length}`);
    console.info(`大写: ${value.toUpperCase()}`);
  } else if (typeof value === 'number') {
    // 编译器知道value是number类型
    console.info(`数值: ${value.toFixed(2)}`);
    console.info(`平方: ${value * value}`);
  } else if (typeof value === 'boolean') {
    // 编译器知道value是boolean类型
    console.info(`布尔值: ${value ? '真' : '假'}`);
  }
}

typeGuardProcessValue('Hello');  // 输出两行：字符串长度: 5 / 大写: HELLO
typeGuardProcessValue(42);       // 输出两行：数值: 42.00 / 平方: 1764
typeGuardProcessValue(true);     // 布尔值: 真
```

### instanceof类型守卫

`instanceof`检查对象是否是某个类的实例（沿原型链逐级匹配），在守卫分支内将类型收窄到该类，可安全访问类的特有成员，也常用于向下转型前的类型确认（详见[子类型](#子类型)）。

<!-- @[instanceof_type_guard](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
class TypeGuardDog {
  public name: string;

  constructor(name: string) {
    this.name = name;
  }

  public bark(): void {
    console.info(`${this.name} barks: Woof!`);
  }
}

class Cat {
  public name: string;

  constructor(name: string) {
    this.name = name;
  }

  public meow(): void {
    console.info(`${this.name} meows: Meow!`);
  }
}

function makeSound(pet: TypeGuardDog | Cat): void {
  console.info(`Pet name: ${pet.name}`);

  if (pet instanceof TypeGuardDog) {
    // 编译器知道pet是TypeGuardDog类型
    pet.bark();
  } else if (pet instanceof Cat) {
    // 编译器知道pet是Cat类型
    pet.meow();
  }
}

let myDog = new TypeGuardDog('Buddy');
let myCat = new Cat('Whiskers');

makeSound(myDog); // 输出两行：Pet name: Buddy / Buddy barks: Woof!
makeSound(myCat); // 输出两行：Pet name: Whiskers / Whiskers meows: Meow!
```

## 类型断言

类型断言告知编译器“把这个值当作指定类型”使用。ArkTS中`as`是类型断言的唯一语法（`value as Type`），不支持尖括号语法`<Type>value`。对可能为空的值，可用非空断言运算符（`!`）断言其不为`null`或`undefined`，其用法与使用限制见[非空断言运算符](arkts-language-guide-basic-operators.md#非空断言运算符)。

### as关键字语法

断言常用于超类型到子类型的向下转型，或将宽泛类型的值断言为具体类型。

<!-- @[as_type_assertion](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
interface UserInfo {
  id: number;
  name: string;
}

let user: UserInfo = { id: 1, name: 'Alice' };

// 向上转型：子类型到超类型，隐式完成
let obj: Object = user;

// 向下转型：超类型到子类型，使用as断言
let restored: UserInfo = obj as UserInfo;
console.info(`${restored.name}`); // 'Alice'

// 断言为联合类型
let mixed: Object = 42;
let unionValue: number | string = mixed as number | string;
```

### 类型断言与数据转换的区别

类型断言不改变值本身，仅按目标类型使用；数据转换（如`Number()`、`String()`）在运行时真正改变值的类型。需要改变数据类型时应使用转换函数，而非断言。

<!-- @[assertion_vs_conversion](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
let convValue: Object = '123';

// 类型断言：不改变值，仅按目标类型使用
let text: string = convValue as string; // 运行时值确实是string，断言成功
console.info(`${text.length}`);     // 3

// 数据转换：运行时真正转换数据类型
let num: number = Number('123');
console.info(`${num.toFixed(2)}`); // 123.00
```

### 类型断言的使用限制

类型断言受两层限制。编译期，不相关的类型之间不能断言；运行时，断言类型与实际类型不匹配时，访问目标类型特有的方法会触发运行时错误，属性访问则返回undefined。因此优先使用类型守卫收窄类型，守卫分支内无需断言；确需断言时，应先确保值的实际类型与断言类型一致。

<!-- @[assertion_runtime_check](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
class ShapeBase {
  public name: string = 'shape';
}

class RoundShape extends ShapeBase {
  public draw(): void {
    console.info(`draw ${this.name}`);
  }
}

let checkShape: ShapeBase = new ShapeBase();

let wrongCircle: RoundShape = checkShape as RoundShape;
// wrongCircle.draw(); // 运行时错误：调用RoundShape成员会触发运行时类型检查失败

// 正确做法：先确认实际类型再访问
if (checkShape instanceof RoundShape) {
  checkShape.draw();
}
```
