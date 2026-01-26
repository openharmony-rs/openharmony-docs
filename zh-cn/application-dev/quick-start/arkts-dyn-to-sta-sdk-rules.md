# ArkTS-Sta SDK迁移规则

## 可选方法已弃用

**规则：** `sdk-optional-methods`

**规则解释：**

ArkTS-Sta不支持类中的可选方法。

**变更原因：**

在ArkTS-Sta中，类的方法由所有实例共享。增加可选方法会增加开发者判断空值的成本，从而影响性能。

**适配建议：**

用可选属性代替可选方法。

**示例：**

ArkTS-Dyn
```typescript
// ArkTS-Dyn API定义
interface NativeMediaPlayerBridge {
  resumePlayer?(): void
}

// ArkTS-Dyn应用代码
class MediaPlayer implements NativeMediaPlayerBridge {
  resumePlayer?(): void {} // ArkTS-Sta中不支持
}
const player1 = new MediaPlayer();
```

ArkTS-Sta
```typescript
// ArkTS-Sta API定义
type ResumePlayerFn = () => void;
interface NativeMediaPlayerBridge {
    resumePlayer?: ResumePlayerFn;
}

// ArkTS-Sta应用代码
class MediaPlayer implements NativeMediaPlayerBridge {
    resumePlayer?: ResumePlayerFn;  // 用可选属性代替
    constructor(resumePlayer?: ResumePlayerFn) {
        this.resumePlayer = resumePlayer;
    }
}
const player1 = new MediaPlayer(() => { });
```

## 限制void类型的使用场景

**规则：** `sdk-limited-void-type`

**规则解释：**

在ArkTS-Dyn中，`void`类型可用于类型声明、类型断言、函数返回类型、泛型类型等场景。

在ArkTS-Sta中，`void`类型只能用作方法的返回类型和泛型类型，并且void类型函数的返回值不能作为值传递。

**变更原因：**

ArkTS-Sta对`void`类型的语义进行了收紧，限制其使用场景以增强类型安全性。

**适配建议：**

请使用undefined代替void。

**示例：**

ArkTS-Dyn
```typescript
// ArkTS-Dyn API定义
type AsyncOrVoidMethod = () => Promise<void> | void;

// ArkTS-Dyn应用代码
const syncFunction: AsyncOrVoidMethod = () => {
  console.info("This is a sync function");
  // 隐式返回void
};

const asyncFunction: AsyncOrVoidMethod = async () => {
  console.info("This is an async function");
  // 隐式返回void
};

async function test() {
  syncFunction();
  await asyncFunction();
}
```

ArkTS-Sta
```typescript
// ArkTS-Sta API定义
type SyncOrVoidMethod = () => undefined; 
type AsyncOrVoidMethod = () => Promise<void>; 

// ArkTS-Sta应用代码
const syncFunction: SyncOrVoidMethod = () => {
  console.info("This is a sync function");
  return undefined; // 必须明确返回undefined
};

const asyncFunction: AsyncOrVoidMethod = async () => {
  console.info("This is an async function");
  return undefined; // 必须明确返回undefined
};

async function test() {
  syncFunction();
  await asyncFunction();
}
```

## 对象名称不可以重复

**规则：** `sdk-no-decl-with-duplicate-name`

**规则解释：**

在ArkTS-Sta中，所有对象不再作为全局对象，而是置于各自的模块中，对象名称不可以重复。

**变更原因：**

在ArkTS-Sta中，模块化开发成为核心特性之一，所有对象不再作为全局对象，而是位于各自的模块中。开发者需要通过import语句显式引入后使用。这一变化提升了代码的可维护性和可扩展性，同时避免了全局命名空间污染。

**适配建议：**

import同名对象时用别名来避免冲突。

**示例：**

ArkTS-Dyn
```typescript
// ArkTS-Dyn
// a.ts
export declare interface LinearGradient {}
export declare class LinearGradient {}

// ArkTS-Dyn应用代码
import { LinearGradient } from './a';
const lg: LinearGradient = {};
const lg2: LinearGradient = new LinearGradient();
```

ArkTS-Sta
```typescript
// ArkTS-Sta，分别放在两个模块中
// @ohos.arkui.a.d.ets
declare interface LinearGradient {}
export { LinearGradient }
// @ohos.arkui.b.d.ets
declare class LinearGradient {}
export { LinearGradient }

// ArkTS-Sta应用代码
import { LinearGradient } from '@ohos.arkui.a.d.ets';
import { LinearGradient as LinearGradientClass } from '@ohos.arkui.b.d.ets';
const lg: LinearGradient = {};
const lg2: LinearGradientClass = new LinearGradientClass();
```

## `attributeValue`方法不再需要传入泛型参数

**规则：** `sdk-no-props-by-index`

**规则解释：**

ArkTS-Sta中，`attributeValue`方法不再需要传入泛型参数。

**变更原因：**

方法签名变更。

**适配建议：**

请删除attributeValue中的泛型参数。

**示例：**

ArkTS-Dyn
```typescript
// a.ts ArkTS-Dyn API定义 
export declare interface ElementAttributeValues {
  description: string;
  checkable: boolean;
}
export declare function attributeValue<T extends keyof ElementAttributeValues>(p: ElementAttributeValues[T]): void;

// ArkTS-Dyn应用代码
import { ElementAttributeValues, attributeValue } from './a';
attributeValue<'checkable'>(true);
```

ArkTS-Sta
```typescript
// a.ets ArkTS-Sta API定义
export declare interface ElementAttributeValues {
    description: string; 
    checkable: boolean;
}
export declare function attributeValue(p: string | boolean): void;

// ArkTS-Sta应用代码
import { ElementAttributeValues, attributeValue } from './a.ets';
attributeValue(true);
```

## 对象的属性名称必须是有效标识符

**规则：** `sdk-no-literal-as-property-name`

**规则解释：**

ArkTS-Sta中，对象的属性名称必须是有效标识符，不支持使用单引号和连字符。

**变更原因：**

在ArkTS-Sta中，对象的属性名不能使用数字或字符串，以增强对边界场景的约束。

**适配建议：**

将属性名从字符串改为标识符。

**示例：**

ArkTS-Dyn
```typescript
// ArkTS-Dyn API定义
interface RequestHeaders {
    'authorization'?: string;
    'content-type': string;
    'x-custom-header': string
};
// ArkTS-Dyn应用代码
const headers: RequestHeaders = {
    'content-type': 'application/json',
    'x-custom-header': 'custom-value',
    'authorization': 'Bearer your-token-here'
};
```

ArkTS-Sta
```typescript
// ArkTS-Sta API定义
interface RequestHeaders {
    authorization?: string;
    contentType: string;
    xCustomHeader: string
};

// ArkTS-Sta应用代码
const headers: RequestHeaders = {
    contentType: 'application/json', // 必填
    xCustomHeader: 'my-custom-value', // 必填
    authorization: 'Bearer your-token-here'
};
```

## 构造类型已弃用

**规则：** `sdk-constructor-funcs`


**规则解释：**

ArkTS-Sta不支持构造函数类型，需要将使用构造函数类型的地方改为lambda函数。

**变更原因：**

移除构造函数类型主要基于静态类型安全和运行时性能优化考虑。

**适配建议：**

将使用构造函数类型的地方改为lambda函数。

**示例：**

ArkTS-Dyn
```typescript
// a.ts ArkTS-Dyn API定义
export declare class User {}
export declare class DatabaseQuery<T> {
  constructor(entityClass: new () => T) ;
}

// ArkTS-Dyn应用代码
import { User, DatabaseQuery } from './a';
const userQuery = new DatabaseQuery(User);
```

ArkTS-Sta
```typescript
// a.ets ArkTS-Sta API定义
export declare class User {}
export declare function createInstence<T>(): T;
export declare class DatabaseQuery<T> {
  constructor(entityClass: () => T);
}

// ArkTS-Sta应用代码
import { createInstence, User, DatabaseQuery } from './a.ets';
const userQuery = new DatabaseQuery<User>(createInstence);
```

## number类型转换为具体的int/long/double类型

**规则：** `sdk-api-num2int`

**规则解释：**

在ArkTS-Dyn中，只有一种数字类型number（与JS/TS相同），该类型实际上是双精度浮点数double，整型字面量会被转化为双精度浮点数来存储。虚拟机会对整型字面量进行优化处理，但总体而言，整型操作时使用独立类型性能更优。

在ArkTS-Sta中，数字类型被区分为了多种，包括byte、char、short、int、long、float、double等；number类型因为等价于double也被保留。

ArkTS-Sta和ArkTS-Dyn在数字类型系统上存在差异。

* ArkTS-Dyn中整型字面量默认为number(double)类型，而ArkTS-Sta中为int类型。这种语义上的变化可能会导致某些表达式或者操作的结果不同。例如，ArkTS-Dyn中1/2表达式结果为0.5，ArkTS-Sta中因为是int类型字面量相除，结果是0。
* Array和Tuple等类型的index在ArkTS-Dyn中可以是任意类型，ArkTS-Sta中必须是非负的整数类型。
* 由于性能原因，ArkTS-Dyn的SDK API中使用的是number类型，但是实际上处理的是int类型操作的API。在ArkTS-Sta的SDK API中，将其入参和返回值修改为了int或者long类型。这样能大大提高SDK API的执行性能。

**变更原因：**

在ArkTS-Sta中，为提升性能与类型安全，将单一的number类型细化为多种具体数字类型。

**适配建议：**

将仅用于整型操作的变量类型改为int或long，否则在API调用处使用.toInt()等方法进行显式转换。

**示例：**

**例一：直接调用SDK API的函数或方法**

ArkTS-Dyn

```typescript
// ArkTS-Dyn API定义
class A {
  foo(a: number): number {
    return 1;
  }
}

// 应用代码
const test0: A = new A()

function test() {
  let a: number = 1;
  let b: number = 2;
  let c: number = 3;
  let d: number = 101 / b;
  c = 1.2;
  let e: number = 1.2;

  let a1: number = test0.foo(a);
  let b1: number = test0.foo(b);
  let c1: number = test0.foo(c);
  let e1: number = test0.foo(e);

  test0.foo(1);
  test0.foo(1.0);
  test0.foo(1.1);

  let x: number = a1;
  let y: number = b1 / 7;
  let z: number = c1;
  z = 1.1;
}
```

**参数场景解析：**

1. 从API foo的调用触发，变量a在其生命周期内始终作为int类型使用，因此可以将a声明为int。
2. 在处理变量b时，发现b用于除法运算并赋值给d，因此b不能声明为int。在调用foo时，需要将b转换为int。
3. 变量c被重新赋值了浮点数字面量，需要在调用处转换为int。
4. 变量e在声明处就被赋值了浮点数字面量，需要在调用处转换为int。
5. foo直接传入字面量，如果是整型字面量，无需修改，如果是1.0这样的浮点数字面量，修改为foo(1); 如果是1.1这样的字面量，修改为(1.1).toInt。
6. 对于参数的场景，不建议对number类型的参数进行修改；建议在参数传入时调用toInt或toLong。

**返回值场景解析：**

1. 变量a1用于接收返回值，始终作为int使用，然后将其赋值给变量x，x始终作为int使用，那么a1和x都应该声明int。
2. b1参与了除法操作，y的赋值表达式中有除法，它们都需要声明为number。
3. 将c1赋值给z后，z又被赋值为浮点字面量。由于int类型可以赋值给number类型变量，c1可以声明为int，但z必须保留为number。
4. 因为e1当做int使用，所以声明改为int。
5. 对于返回值的场景，因为int/long可以直接转换为number/double用，建议对返回值类型不做变化。

ArkTS-Sta

```typescript
// ArkTS-Sta API定义
class A {
  foo(a: int): int {
    return 1;
  }
}

// 应用代码
const test0: A = new A();

function test() {
  let a: int = 1;
  let b: number = 2;
  let c: number = 3;
  let d: number = 101 / b;
  c = 1.2;
  let e: number = 1.2;

  let a1: int = test0.foo(a);
  let b1: number = test0.foo(b.toInt());
  let c1: int = test0.foo(c.toInt());
  let e1: int = test0.foo(e.toInt());

  test0.foo(1);
  test0.foo(1);
  test0.foo(1.1.toInt());

  let x: int = a1;
  let y: number = b1 / 7;
  let z: number = c1;
  z = 1.1;
}
```

**例二：调用API是属性和变量的情况**

ArkTS-Dyn

```typescript
// ArkTS-Dyn API定义
class A {
    static x: number = 1;
}

// 应用代码
let a: number = A.x;
let b: number = A.x;
let c: number = A.x;
let d: number = 101 / b;
c = 1.2;
```

ArkTS-Sta

```typescript
// ArkTS-Sta API定义
class A {
    static x: int = 1;
}

// 应用代码
let a: int = A.x; 
let b: number = A.x;  // b参与除法，依然保留为number类型
let c: number = A.x;  // c被再次赋值了浮点数字面量，依然保留为number类型
let d: number = 101 / b;
c = 1.2;
```

**例三：API是interface/class属性，并且interface/class的对象使用字面量赋值**

ArkTS-Dyn

```typescript
// ArkTS-Dyn SDK API
interface A {
    a: number;
    b: number;
}

function foo(a: number): number{
    return 1;
}

// 场景1
let x0: A = {
    a: 1,
    b: 2
}

foo(x0.a)
foo(x0.b)

// 场景2
let x1: A = {
    a: 1,
    b: 1.1
}

foo(x1.a)
foo(x1.b)

// 场景3
let x2: A = {
    a: 1,
    b: 2/3
}

foo(x2.a)
foo(x2.b)

// 场景4
let x3: A = {
    a: 3 / 4,
    b: 2 / 3
}

foo(x3.a)
foo(x3.b)
```

ArkTS-Sta

```typescript
// ArkTS-Sta SDK API
interface A {
    a: number;
    b: int;
}

function foo(a: int): int{
    return 1;
}

// 场景1
let x0: A = {
    a: 1,
    b: 2
}

foo(x0.a.toInt()) // x.a为number类型，赋值给int类型的参数，需要调用toInt()
foo(x0.b) // x.b为int类型

// 场景2
let x1: A = {
    a: 1,
    b: (1.1).toInt() // 需要转化为int，但是实际上如果有这种情况，SDK API的类型不应该改为int
}

foo(x1.a.toInt()) // x.a为number类型，赋值给int类型的参数，需要调用toInt()
foo(x1.b) // x.b为int类型

// 场景3
let x2: A = {
    a: 1,
    b: 2/3 // 不用修改，因为2/3在ArkTS-Sta会自动截取为int
}

foo(x2.a.toInt()) // x.a为number类型，赋值给int类型的参数，需要调用toInt()
foo(x2.b) // x.b为int类型

// 场景4
let x3: A = {
    a: 3.0 / 4, // a的类型为number，这里需要将除数修改为浮点数字面量，否则结果会丢失精度
    b: 2 / 3 // 不用修改，因为2/3在ArkTS-Sta会自动截取为int
}

foo(x3.a.toInt()); // x.a为number类型，赋值给int类型的参数，需要调用toInt()
foo(x3.b); // x.b为int类型

// 以上是interface的场景，如果是class是一样的
```


## 异步生命周期变更

**规则：** `sdk-ability-asynchronous-lifecycle`

**规则解释：**

[onDestroy](../application-models/uiability-lifecycle.md#ondestroy)是UIAbility生命周期回调，当UIAbility被销毁时，系统会触发该回调。

开发者可以在该生命周期中执行资源清理等相关操作，使用同步回调或Promise异步回调。

在ArkTS-Sta中，void无法作为联合类型，需要把onDestroy()拆分为两个接口：同步调回onDestroy(): void或异步调回onDestroyAsync(): Promise\<void\>。

**变更原因：**

ArkTS-Sta对void类型的语义进行了收紧，限制其使用场景以增强类型安全性。

**适配建议：**

根据原onDestroy实现，将其拆分到对应的onDestroy或onDestroyAsync接口中。

**示例：**

ArkTS-Dyn

```
import { UIAbility } from '@kit.AbilityKit';

function sleep(ms: number): Promise<void> {
  return new Promise((resolve, reject) => {
    setTimeout(resolve, ms)
  })
}

export default class MyUIAbility extends UIAbility {
  async onDestroy(): Promise<void> {
    console.info('testTag', '%{public}s', 'Ability onDestroy');
    return sleep(1000);
  }
}
```

ArkTS-Sta

```
import { UIAbility } from '@kit.AbilityKit';

function sleep(ms: double): Promise<void> {
  return new Promise<void>((resolve, reject) => {
    setTimeout(resolve)
  })
}

class MyUIAbility extends UIAbility {
  onDestroyAsync(): Promise<void> {
    console.info('testTag', '%{public}s', 'Ability onDestroy');
    return sleep(1000);
  }
}
```

## 扫描生命周期监听变更

**规则：** `sdk-ability-lifecycle-monitor`

**规则解释：**

在ArkTS-Sta中，UIAbility需要用新的接口StaticAbilityLifecycleCallback监听。

**变更原因：**

ArkTS-Sta的UIAbility不支持使用[AbilityLifecycleCallback](../reference/apis-ability-kit/js-apis-app-ability-abilityLifecycleCallback.md)监听UIAbility。

**适配建议：**

在ArkTS-Sta中，使用接口StaticAbilityLifecycleCallback监听UIAbility。

**示例：**

ArkTS-Dyn

```
import { UIAbility, AbilityStage, AbilityLifecycleCallback} from '@kit.AbilityKit';

class MyAbilityStage extends AbilityStage {
  onCreate() {
    let AbilityLifecycleCallback: AbilityLifecycleCallback = {
      onAbilityCreate(ability) {
        console.info(`AbilityLifecycleCallback onAbilityCreate ability: ${ability}`);
      },
      onWindowStageCreate(ability, windowStage) {
        console.info(`AbilityLifecycleCallback onWindowStageCreate ability: ${ability}`);
        console.info(`AbilityLifecycleCallback onWindowStageCreate windowStage: ${windowStage}`);
      },
      onWindowStageActive(ability, windowStage) {
        console.info(`AbilityLifecycleCallback onWindowStageActive ability: ${ability}`);
        console.info(`AbilityLifecycleCallback onWindowStageActive windowStage: ${windowStage}`);
      },
      onWindowStageInactive(ability, windowStage) {
        console.info(`AbilityLifecycleCallback onWindowStageInactive ability: ${ability}`);
        console.info(`AbilityLifecycleCallback onWindowStageInactive windowStage: ${windowStage}`);
      },
      onWindowStageDestroy(ability, windowStage) {
        console.info(`AbilityLifecycleCallback onWindowStageDestroy ability: ${ability}`);
        console.info(`AbilityLifecycleCallback onWindowStageDestroy windowStage: ${windowStage}`);
      },
      onAbilityDestroy(ability) {
        console.info(`AbilityLifecycleCallback onAbilityDestroy ability: ${ability}`);
      },
      onAbilityForeground(ability) {
        console.info(`AbilityLifecycleCallback onAbilityForeground ability: ${ability}`);
      },
      onAbilityBackground(ability) {
        console.info(`AbilityLifecycleCallback onAbilityBackground ability: ${ability}`);
      },
      onAbilityContinue(ability) {
        console.info(`AbilityLifecycleCallback onAbilityContinue ability: ${ability}`);
      }
    }
    // 1.通过context属性获取applicationContext
    let applicationContext = this.context.getApplicationContext();
    // 2.通过applicationContext注册监听应用内生命周期
    let lifecycleId = applicationContext.on('abilityLifecycle', AbilityLifecycleCallback);
    console.info(`registerAbilityLifecycleCallback lifecycleId: ${lifecycleId}`);
  }
}

```

ArkTS-Sta

```
import { UIAbility, AbilityStage, StaticAbilityLifecycleCallback} from '@kit.AbilityKit';

class MyAbilityStage extends AbilityStage {
  onCreate() {
    let StaticAbilityLifecycleCallback: StaticAbilityLifecycleCallback = {
      onAbilityCreate(ability) {
        console.info(`StaticAbilityLifecycleCallback onAbilityCreate ability: ${ability}`);
      },
      onWindowStageCreate(ability, windowStage) {
        console.info(`StaticAbilityLifecycleCallback onWindowStageCreate ability: ${ability}`);
        console.info(`StaticAbilityLifecycleCallback onWindowStageCreate windowStage: ${windowStage}`);
      },
      onWindowStageActive(ability, windowStage) {
        console.info(`StaticAbilityLifecycleCallback onWindowStageActive ability: ${ability}`);
        console.info(`StaticAbilityLifecycleCallback onWindowStageActive windowStage: ${windowStage}`);
      },
      onWindowStageInactive(ability, windowStage) {
        console.info(`StaticAbilityLifecycleCallback onWindowStageInactive ability: ${ability}`);
        console.info(`StaticAbilityLifecycleCallback onWindowStageInactive windowStage: ${windowStage}`);
      },
      onWindowStageDestroy(ability, windowStage) {
        console.info(`StaticAbilityLifecycleCallback onWindowStageDestroy ability: ${ability}`);
        console.info(`StaticAbilityLifecycleCallback onWindowStageDestroy windowStage: ${windowStage}`);
      },
      onAbilityDestroy(ability) {
        console.info(`StaticAbilityLifecycleCallback onAbilityDestroy ability: ${ability}`);
      },
      onAbilityForeground(ability) {
        console.info(`StaticAbilityLifecycleCallback onAbilityForeground ability: ${ability}`);
      },
      onAbilityBackground(ability) {
        console.info(`StaticAbilityLifecycleCallback onAbilityBackground ability: ${ability}`);
      },
      onAbilityContinue(ability) {
        console.info(`StaticAbilityLifecycleCallback onAbilityContinue ability: ${ability}`);
      }
    }
    // 1.通过context属性获取applicationContext
    let applicationContext = this.context.getApplicationContext();
    // 2.通过applicationContext注册监听应用内生命周期
    let lifecycleId = applicationContext.on('abilityLifecycle', StaticAbilityLifecycleCallback);
    console.info(`registerStaticAbilityLifecycleCallback lifecycleId: ${lifecycleId}`);
  }
}
```

## 重载API变更

**规则：** `sdk-api-static-overload`

**规则解释：**

ArkTS-Sta重载实现方式发生变化，ArkTS-Dyn部分API的名称和使用方式需要变化。

**变更原因：**

为了增强运行时的性能和效率，ArkTS-Sta采用静态化方式实现重载。

**适配建议：**

在调用ArkTS-Dyn相关API时，需同步更新接口名称及参数传递方式。

**示例：**

ArkTS-Dyn

```
// ArkTS-Dyn API定义
on(type: 'update', callback: () => void): void;

// 应用代码
import { pasteboard } from '@kit.BasicServicesKit';

const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
let listener = () => {
  console.info('The system pasteboard has changed.');
};
systemPasteboard.on('update', listener);
```

ArkTS-Sta

```
// ArkTS-Sta API定义
onUpdate(callback: UpdateCallback): void

// 应用代码
import { pasteboard } from '@kit.BasicServicesKit';

const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
let listener = () => {
  console.info('The system pasteboard has changed.');
};
systemPasteboard.onUpdate(listener);
```

## 不支持ConvertXML

**规则：** `arkts-interop-js2s-create-js-instance`

**规则解释：**

ArkTS-Sta不能直接实例化JS对象。

**变更原因：**

ArkTS-Sta不能直接实例化JS对象，不支持ConvertXML解析XML文本后创建JsObject对象添加XML内容返回。

**适配建议：**

使用ArkTS-Dyn提供的xml.XmlPullParser来解析XML并获取属性[XML解析](../arkts-utils/xml-parsing.md)。

**示例：**

ArkTS-Dyn

```typescript
import { convertxml } from '@kit.ArkTS';

try {
  let xml =
    '<?xml version="1.0" encoding="utf-8"?>' +
    '<note importance="high" logged="true">' +
    '   <title>Hello\r\nWorld</title>' +
    '   <todo><![CDATA[Work\r\n]]></todo>' +
    '</note>';
  let conv = new convertxml.ConvertXML();
  let options: convertxml.ConvertOptions = {
    trim: false, declarationKey: "_declaration",
    instructionKey: "_instruction", attributesKey: "_attributes",
    textKey: "_text", cdataKey: "_cdata", doctypeKey: "_doctype",
    commentKey: "_comment", parentKey: "_parent", typeKey: "_type",
    nameKey: "_name", elementsKey: "_elements"
  }
  let result = JSON.stringify(conv.fastConvertToJSObject(xml, options));
  console.info(result);
} catch (e) {
  console.error((e as Object).toString());
}
// 输出(宽泛型)
// {"_declaration":{"_attributes":{"version":"1.0","encoding":"utf-8"}},"_elements":[{"_type":"element","_name":"note","_attributes":{"importance":"high","logged":"true"},"_elements":[{"_type":"element","_name":"title","_elements":[{"_type":"text","_text":"Hello\nWorld"}]},{"_type":"element","_name":"todo","_elements":[{"_type":"cdata","_cdata":"Work\n"}]}]}]}
```

ArkTS-Sta

```typescript
import { xml, util } from '@kit.ArkTS'; // 需要使用util模块函数对文本编码

let strXml: string =
'<?xml version="1.0" encoding="utf-8"?>' +
  '<note importance="high" logged="true">' +
  '<title>Play</title>' +
  '<lens>Work</lens>' +
  '</note>';
let textEncoder: util.TextEncoder = new util.TextEncoder();
let arrBuffer: Uint8Array = textEncoder.encodeInto(strXml); // 对数据进行编码，防止中文字符乱码
// 基于ArrayBuffer构造XmlPullParser对象
let that: xml.XmlPullParser = new xml.XmlPullParser(arrBuffer.buffer as object as ArrayBuffer, 'UTF-8');

// 自定义回调函数，本例直接打印出标签及标签值。
function func(name: string, value: string): boolean {
  if (name == 'note') {
    console.info(name);
  }
  if (value == 'Play' || value == 'Work') {
    console.info('    ' + value);
  }
  if (name == 'title' || name == 'lens') {
    console.info('  ' + name);
  }
  return true; // true:继续解析 false:停止解析
}

let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:true, tagValueCallbackFunction:func};
that.parseXml(options);
// 输出结果如下
//note
//  title
//    Play
//  title
//  lens
//    Work
//  lens
//note
```

## 静态类型null/undefined需要显示声明

**规则解释：**

在ArkTs-Sta中null/undefined需要显示声明。

**变更原因：**

1. 提升稳定性：在编译阶段拦截空指针异常，消除运行时的 Null Pointer Exception。
2. 代码自注释：强制声明 null/undefined 使接口意图更明确，降低维护成本。
3. 性能优化：明确的类型边界便于编译器生成更高效的机器码。

**适配建议：**

用户对对象进行null/undefined容错处理。

**示例**

ArkTS-Dyn

示例一：返回值

```
// ArkTS-Dyn API定义
declare function getValue(): number;

// ArkTS-Dyn应用代码
let v: number = getValue(key);
```

示例二：属性
```
// ArkTS-Dyn API定义
interface MyObject {
    name: string;
}
declare function getObject(): MyObject;
// ArkTS-Dyn应用代码
let obj: MyObject = getObject();
let myName: string = obj.name;
```

示例三：回调入参
```
// ArkTS-Dyn API定义
interface Activity {
	onCreate(result: string):void;
}
// ArkTS-Dyn应用代码
class MyActivity implements Activity {
    onCreate(result: string) {
        console.log(result.toUpperCase());
    }
}
```


ArkTS-Sta

示例一：返回值

```
// ArkTS-Sta API定义
declare function getValue(): number | null;// 显示声明null

// ArkTS-Sta应用代码
let tmp: number | null = getValue(); 

if (tmp == null) { // 判断返回值是null的情况
    // todo
    return;
}
let v: number = tmp as number;   
```

示例二：属性
```
// ArkTS-Sta API定义
interface MyObject {
    name: string | null;
}
declare function getObject(): MyObject;
// ArkTS-Sta应用代码
let obj: MyObject = getObject();
let myName: string = obj.name as string;
```

示例三：回调入参
```
// ArkTS-Sta API定义
interface Activity {
	onCreate(result: string|null):void;
}
// ArkTS-Sta应用代码
class MyActivity implements Activity {
    onCreate(result: string|null) {
        console.log(result?.toUpperCase());
    }
}
```

## Any/Object初始化字面量和参数嵌套修改

**规则解释：**

1. ArkTS-Sta下，不支持Object类型初始化为字面量。
2. 由于ArkTS-Sta的any会被修改为`undefined | null| Object`和静态复用，所以也会出现这个问题。

**变更原因：**

ArkTS-Sta下，不支持Object类型初始化为字面量。

**示例：**

ArkTS-Dyn

示例一：数据结构固定，层级和每层的属性都固定。

```
// ArkTS-Dyn API定义
declare function getValue(obj: Object): number;

// ArkTS-Dyn应用代码
let obj: Object = {
    'x': 1,
    'y': {
        'xx': 0
    }
} 
let v: number = getValue(obj);
```

示例二：层级有约束，每层的属性数量没有限制。

```
// ArkTS-Dyn API定义
declare function getValue(obj: Object): number;

// ArkTS-Dyn应用代码
let obj: Object = {
    'x': 1
} 
let v: number = getValue(obj);
```

示例三：层级有约束，每层的属性数量没有限制。

```
// ArkTS-Dyn API定义
declare function getValue(obj: Object): number;

// ArkTS-Dyn应用代码
let obj: Object = {
    'x': 1,
    'y': {
        'xx': 0,
        'yy': {
            'xxx': 'harmonyos',
            'yyy': [
                'arkui',
                'ability',
                'arkweb'
            ]
        }
    }
} 
let v: number = getValue(obj);
```

ArkTS-Sta

示例一：数据结构固定，层级和每层的属性都固定。

```
// ArkTS-Sta API定义
interface YType {
    xx: number;
}

interface MyType {
    x: number;
    y: YType;
}
declare function getValue(type: MyType): number;

// ArkTS-Sta应用代码
let type: MyType = {
    'x': 1,
    'y': {
        'xx': 0
    }
} 
let v: number = getValue(type);  
```

示例二：层级有约束，每层的属性数量没有限制。

```
// ArkTS-Sta API定义
declare function getValue(type: Record<string, number>): number;

// ArkTS-Sta应用代码
// 使用 Record 替代 Object
let type: Record<string, number> = {
    'x': 1  // x 需要加引号，改成 'x'
} 
let v: number = getValue(type);  
```

示例三：层级有约束，每层的属性数量没有限制。

```
// ArkTS-Sta API定义
type RecordData = undefined | null | Object | Record<string, RecordData> | Array<RecordData>;
declare function getValue(type: RecordData): number;

// ArkTS-Sta应用代码
let type: RecordData = {
    'x': 1,
    'y': {
        'xx': 0,
        'yy': {
            'xxx': 'harmonyos',
            'yyy': [
                'arkui',
                'ability',
                'arkweb'
            ]
        }
    }
}
let v: number = getValue(type);  
```

## Interface方法定义区分应用主动调用和操作系统回调

**规则解释：**

1. 开发者通过继承的方式使用，必须和父类interface一致，否则编译报错。
2. 方法类的API，父节点是interface，该方法为操作系统回调应用的方法，使用属性的方式定义。（例：fn:()=>void;）
3. 方法类的API，父节点是interface，该方法为应用主动调用操作系统的方法，使用函数的方式定义。(例：fn():void;)

**变更原因：**

1. 在满足使用场景的情况下，建议尽量使用成员方法。
2. 成员方法优势：对象体积小，方法不可被更改。
3. 函数属性优势：动态可修改，动态this灵活。

**示例：**

ArkTS-Dyn


示例一：函数属性修改为成员方法

```
// ArkTS-Dyn API定义
declare interface People {
    getName: () => string   // 函数属性
}

// ArkTS-Dyn应用代码
class Person implements People {
    getName = (): string => { // 函数属性方式实现
        return "固定的名字";
    };
}
```

示例二：成员方法修改为函数属性

```
// ArkTS-Dyn API定义
declare interface People {
    getName(): string       // 成员方法
}

// ArkTS-Dyn应用代码
class Person implements People {
    getName(): string { // 成员方法方式实现
        return "固定的名字";
    }
}
```

ArkTS-Sta

示例一：函数属性修改为成员方法

```
// ArkTS-Sta API定义
declare interface People {
    getName(): string       //这里修改为成员方法
}

// ArkTS-Sta应用代码
class Person implements People {
    getName(): string {   // 应用必须成员方法实现
        return "固定的名字";
    }
}
```

示例二：成员方法修改为函数属性

```
// ArkTS-Sta API定义
type GetNameFunc = () => string;
declare interface People {
    getName: GetNameFunc;  // 这里修改使用定义好的类型函数方法
}

// ArkTS-Sta应用代码
class Person implements People {
    getName = (): string => { // 这里必须函数属性方式实现
        return "固定的名字";
    };
}
```

## ArkTS-Sta语法关键字避让

**规则解释：**

ArkTS-Sta语法关键字列表，API使用时需要避开语言关键词，以免编译报错。
以下列表中加粗的部分是ArkTS-Sta新增关键字。

| 关键字             |            |              |           |
|-----------------| ---------- | ------------ | --------- |
| **abstract**    | else       | **internal** | static    |
| **as**          | enum       | let          | switch    |
| **async**       | export     | **native**   | super     |
| await           | extends    | new          | this      |
| break           | false      | null         | throw     |
| case            | final      | **overload** | true      |
| class           | for        | **override** | try       |
| const           | function   | **package**  | undefined |
| **constructor** | if         | private      | while     |
| continue        | implements | protected    |           |
| default         | import     | public       |           |
| do              | interface  | return       |           |


| **Any**     |            | **declare**   |
| ----------- | ---------- | ------------- |
| **bigint**  | BigInt     | in            |
| **boolean** | Boolean    | instanceof    |
| **byte**    | **Byte**   | **namespace** |
| **char**    | **Char**   | **out**       |
| **double**  | **Double** | **readonly**  |
| **float**   | **Float**  | **type**      |
| **int**     | **Int**    | typeof        |
| **long**    | **Long**   |               |
| **number**  | Number     |               |
| **Object**  | object     |               |
| **short**   | Short      |               |
| **string**  | String     |               |
| void        |            |               |

**变更原因：**

语言演进需要。

**示例：**

ArkTS-Dyn
```
// ArkTS-Dyn API定义
export interface Float {
    value: number;
    precision: number;
}

// ArkTS-Dyn应用代码
interface Result extends Float {
    age: number;
}
```

ArkTS-Sta

```
// ArkTS-Sta API定义
export interface FloatResult {
    value: number;
    precision: number;
}

// ArkTS-Sta 应用代码
interface Result extends FloatResult {
    age: number;
}
```