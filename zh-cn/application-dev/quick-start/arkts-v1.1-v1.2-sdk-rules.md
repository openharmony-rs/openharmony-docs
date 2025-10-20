# ArkTS1.2SDK迁移规则

## 可选方法已弃用

**规则：** `sdk-optional-methods`

**规则解释：**

ArkTS1.2不支持类中的可选方法。

**变更原因：**

在ArkTS1.2中，类的方法由所有实例共享。增加可选方法会增加开发者判断空值的成本，从而影响性能。

**适配建议：**

用可选属性代替可选方法。

**示例：**

**ArkTS1.1**
```typescript
// ArkTS1.1API定义
interface NativeMediaPlayerBridge {
  resumePlayer?(): void
}

// ArkTS1.1应用代码
import NativeMediaPlayerBridge from 'xxx'
class MediaPlayer implements NativeMediaPlayerBridge {
  resumePlayer?(): void { // ArkTS1.2中不支持
  }
}
const player1 = new MediaPlayer();
```

**ArkTS1.2**
```typescript
// ArkTS1.2API定义
type ResumePlayerFn = () => void;
interface NativeMediaPlayerBridge {
    resumePlayer?: ResumePlayerFn;
}

// ArkTS1.2应用代码
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

在ArkTS1.1中，`void`类型可用于类型声明、类型断言、函数返回类型、泛型类型等场景。

在ArkTS1.2中，`void`类型只能用作方法的返回类型和泛型类型，并且void类型函数的返回值不能作为值传递。

**变更原因：**

ArkTS1.2对`void`类型的语义进行了收紧，限制其使用场景以增强类型安全性。

**适配建议：**

请使用undefined代替void。

**示例：**
 
**ArkTS1.1**
```typescript
// ArkTS1.1API定义
type AsyncOrVoidMethod = () => Promise<void> | void;

// ArkTS1.1应用代码
const syncFunction: AsyncOrVoidMethod = () => {
  console.log("This is a sync function");
  // 隐式返回void
};
```

**ArkTS1.2**
```typescript
// ArkTS1.2API定义
type AsyncOrVoidMethod = () => Promise<void> | undefined;

// ArkTS1.2应用代码
const syncFunction: AsyncOrVoidMethod = () => {
  console.log("This is a sync function");
  return undefined;
};
```

## 对象名称不可以重复

**规则：** `sdk-no-decl-with-duplicate-name`

**规则解释：**

在ArkTS1.2中，所有对象不再作为全局对象，而是置于各自的模块中，对象名称不可以重复。

**变更原因：**

在ArkTS1.2中，模块化开发成为核心特性之一，所有对象不再作为全局对象，而是位于各自的模块中。开发者需要通过import语句显式引入后使用。这一变化提升了代码的可维护性和可扩展性，同时避免了全局命名空间污染。

**适配建议：**

import同名对象时用别名来避免冲突。

**示例：**

**ArkTS1.1**
```typescript
// ArkTS1.1
declare interface LinearGradient {}
declare class LinearGradient {}

// ArkTS1.1应用代码
const lg: LinearGradient = {};
const lg2: LinearGradient = new LinearGradient();
```

**ArkTS1.2**
```typescript
// ArkTS1.2，分别放在两个模块中
// @ohos.arkui.a.d.ts
declare interface LinearGradient {}
export { LinearGradient }
// @ohos.arkui.b.d.ts
declare class LinearGradient {}
export { LinearGradient }

// ArkTS1.2应用代码
import { LinearGradient } from '@ohos.arkui.a.d.ts';
import { LinearGradient as LinearGradientClass } from '@ohos.arkui.b.d.ts';
const lg: LinearGradient = {};
const lg2: LinearGradientClass = new LinearGradientClass();
```

## `attributeValue`方法不再需要传入泛型参数

**规则：** `sdk-no-props-by-index`

**规则解释：**

ArkTS1.2中，`attributeValue`方法不再需要传入泛型参数。

**变更原因：**

方法签名变更。

**适配建议：**

请删除attributeValue中的泛型参数。

**示例：**

**ArkTS1.1**
```typescript
// ArkTS1.1API定义
declare interface ElementAttributeValues {
    description: string;
    checkable: boolean;
}
declare function attributeValue<T extends keyof ElementAttributeValues>(p: ElementAttributeValues[T]): void;

// ArkTS1.1应用代码
attributeValue<'checkable'>(true);
```

**ArkTS1.2**
```typescript
// ArkTS1.2API定义
declare interface ElementAttributeValues {
    description: string;
    checkable: boolean;
}
declare function attributeValue(p: string | boolean): void;

// ArkTS1.2应用代码
attributeValue(true);
```

## 对象的属性名称必须是有效标识符

**规则：** `sdk-no-literal-as-property-name`

**规则解释：**

ArkTS1.2中，对象的属性名称必须是有效标识符，不支持使用单引号和连字符。

**变更原因：**
 
在ArkTS1.2中，对象的属性名不能使用数字或字符串，以增强对边界场景的约束。

**适配建议：**

将属性名从字符串改为标识符。

**示例：**

**ArkTS1.1**
```typescript
// ArkTS1.1API定义
export interface RequestHeaders {
    'authorization'?: string;
    'content-type': string,
    'x-custom-header': string
};
// ArkTS1.1应用代码
const headers: RequestHeaders = {
    'content-type': 'application/json',
    'x-custom-header': 'custom-value',
    'authorization': 'Bearer your-token-here'
};
```

**ArkTS1.2**
```typescript
// ArkTS1.2API定义
export interface RequestHeaders {
    authorization?: string;
    contentType: string;
    xCustomHeader: string;
};

// ArkTS1.2应用代码
const headers: RequestHeaders = {
    contentType: 'application/json',  // 必填
    xCustomHeader: 'my-custom-value' // 必填
};
```

## 构造类型已弃用

**规则：** `sdk-constructor-funcs`


**规则解释：**

ArkTS1.2不支持构造函数类型，需要将使用构造函数类型的地方改为lambda函数。

**变更原因：**

移除构造函数类型主要基于静态类型安全和运行时性能优化考虑。

**适配建议：**

将使用构造函数类型的地方改为lambda函数。

**示例：**

**ArkTS1.1**
```typescript
// ArkTS1.1API定义
declare class User {}
declare class DatabaseQuery<T> {
    constructor(entityClass: new () => T);
}
// ArkTS1.1应用代码
const userQuery = new DatabaseQuery(User);
```

**ArkTS1.2**
```typescript
// ArkTS1.2API定义
declare class User {}
declare function createInstence<T>(): T;
declare class DatabaseQuery<T> {
  constructor(entityClass: () => T);
}

// ArkTS1.2应用代码
const userQuery = new DatabaseQuery<User>(createInstence);
```

## number类型转换为具体的int/long/double类型

**规则：** `sdk-api-num2int`

**规则解释：**

在ArkTS1.1中，只有一种数字类型number（与JS/TS相同），该类型实际上是双精度浮点数double，整型字面量会被转化为双精度浮点数来存储。虚拟机会对整型字面量进行优化处理，但总体而言，整型操作时使用独立类型性能更优。

在ArkTS1.2中，数字类型被区分为了多种，包括byte、char、short、int、long、float、double等；number类型因为等价于double也被保留。

ArkTS1.2和ArkTS1.1在数字类型系统上存在差异。

* ArkTS1.1中整型字面量默认为number(double)类型，而ArkTS1.2中为int类型。这种语义上的变化可能会导致某些表达式或者操作的结果不同。例如，ArkTS1.1中1/2表达式结果为0.5，ArkTS1.2中因为是int类型字面量相除，结果是0。
* Array和Tuple等类型的index在ArkTS1.1中可以是任意类型，ArkTS1.2中必须是非负的整数类型。
* 由于性能原因，ArkTS1.1的SDK API中使用的是number类型，但是实际上处理的是int类型操作的API。在ArkTS1.2的SDK API中，将其入参和返回值修改为了int或者long类型。这样能大大提高SDK API的执行性能。

**变更原因：**

在ArkTS1.2中，为提升性能与类型安全，将单一的number类型细化为多种具体数字类型。

**适配建议：**

将仅用于整型操作的变量类型改为int或long，否则在API调用处使用.toInt()等方法进行显式转换。

**示例：**

**例一：直接调用SDK API的函数或方法**

**ArkTS1.1**

```typescript
// ArkTS1.1API定义
Class A {
    foo(number a): number {
        return 1;
    }
}

// 应用代码
function test() {
   let a: number = 1;
   let b: number = 2;
   let c: number = 3;
   let d: number = 101 / b;
   c = 1.2;
   let e: number = 1.2;

   let a1: number = foo(a); 
   let b1: number = foo(b);
   let c1: number = foo(c);
   let e1: number = foo(e);

   foo(1);
   foo(1.0);
   foo(1.1);
 
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

**ArkTS1.2**

```typescript
// ArkTS1.2API定义
Class A {
    foo(int a): int {
        return 1;
    }
}

// 应用代码
function test() {
   let a: int = 1;
   let b: number = 2;
   let c: number = 3;
   let d: number = 101 / b;
   c = 1.2;
   let e: number = 1.2;

   let a1: int = foo(a); 
   let b1: number = foo(b.toInt());
   let c1: int = foo(c.toInt());
   let e1: int = foo(e.toInt());

   foo(1);
   foo(1);
   foo(1.1.toInt());

   let x: int = a1;
   let y: number = b1 / 7;
   let z: number = c1;
   z = 1.1;
}
```

**例二：调用API是属性和变量的情况**

**ArkTS1.1**

```typescript
// ArkTS1.1API定义
Class A {
    static x: number = 1;
}

// 应用代码
let a: number = A.x;
let b: number = A.x;
let c: number = A.x;
let d: number = 101 / b;
c = 1.2;
```

**ArkTS1.2**

```typescript
// ArkTS1.2API定义
Class A {
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

```typescript
// ArkTS 1.1 SDK API
interface A {
    a: number;
    b: number;
}

// ArkTS 1.2 SDK API
interface A {
    a: number;
    b: int;
}

// ArkTS 1.2 SDK API
function foo(a: int): int{
    return 1;
}


// 场景1
// ArkTS 1.1
let x: A = {
    a: 1,
    b: 2
}
// ArkTS 1.2
// 不用修改
let x: A = {
    a: 1,
    b: 2
}

foo(x.a.toInt()) // x.a为number类型，赋值给int类型的参数，需要调用toInt()
foo(x.b) // x.b为int类型

// 场景2
// ArkTS 1.1
let x: A = {
    a: 1,
    b: 1.1
}
// ArkTS 1.2
let x:A = {
    a: 1,
    b: (1.1).toInt() // 需要转化为int，但是实际上如果有这种情况，SDK API的类型不应该改为int
}

foo(x.a.toInt()) // x.a为number类型，赋值给int类型的参数，需要调用toInt()
foo(x.b) // x.b为int类型

// 场景3
// ArkTS 1.1
let x: A = {
    a: 1,
    b: 2/3
}
// ArkTS 1.2
let x: A = {
    a: 1,
    b: 2/3 // 不用修改，因为2/3在1.2会自动截取为int
}

foo(x.a.toInt()) // x.a为number类型，赋值给int类型的参数，需要调用toInt()
foo(x.b) // x.b为int类型

// 场景4
// ArkTS 1.1
let x: A = {
    a: 3 / 4,
    b: 2 / 3
}
// ArkTS 1.2
let x: A = {
    a: 3.0 / 4, // a的类型为number，这里需要将除数修改为浮点数字面量，否则结果会丢失精度
    b: 2 / 3 // 不用修改，因为2/3在1.2会自动截取为int
}

foo(x.a.toInt()); // x.a为number类型，赋值给int类型的参数，需要调用toInt()
foo(x.b); // x.b为int类型

// 以上是interface的场景，如果是class是一样的
```


## 异步生命周期变更

**规则：** `sdk-ability-asynchronous-lifecycle`

**规则解释：**

[onDestroy](../application-models/uiability-lifecycle.md#ondestroy)是UIAbility生命周期回调，当UIAbility被销毁时，系统会触发该回调。

开发者可以在该生命周期中执行资源清理等相关操作，使用同步回调或Promise异步回调。

在ArkTS1.2中，void无法作为联合类型，需要把onDestroy()拆分为两个接口：同步调回onDestroy(): void或异步调回onDestroyAsync(): Promise\<void\>。

**变更原因：**

ArkTS1.2对void类型的语义进行了收紧，限制其使用场景以增强类型安全性。

**适配建议：**

根据原onDestroy实现，将其拆分到对应的onDestroy或onDestroyAsync接口中。

**示例：**

**ArkTS1.1**

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

**ArkTS1.2**

```
import { UIAbility } from '@kit.AbilityKit';

function sleep(ms: number): Promise<void> {
  return new Promise((resolve, reject) => {
    setTimeout(resolve, ms)
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

在ArkTS1.2中，UIAbility需要用新的接口StaticAbilityLifecycleCallback监听。

**变更原因：**

ArkTS1.2的UIAbility不支持使用[AbilityLifecycleCallback](../reference/apis-ability-kit/js-apis-app-ability-abilityLifecycleCallback.md)监听UIAbility。

**适配建议：**

在ArkTS1.2中，使用接口StaticAbilityLifecycleCallback监听UIAbility。

**示例：**

**ArkTS1.1**

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

**ArkTS1.2**

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

ArkTS1.2重载实现方式发生变化，ArkTS1.1部分API的名称和使用方式需要变化。

**变更原因：**

为了增强运行时的性能和效率，ArkTS1.2采用静态化方式实现重载。

**适配建议：**

在调用ArkTS1.1相关API时，需同步更新接口名称及参数传递方式。

**示例：**

**ArkTS1.1**

```
// ArkTS1.1API定义
on(type: 'update', callback: () => void): void;

// 应用代码
import { pasteboard } from '@kit.BasicServicesKit';

const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
let listener = () => {
  console.info('The system pasteboard has changed.');
};
systemPasteboard.on('update', listener);
```

**ArkTS1.2**

```
// ArkTS1.2API定义
onUpdate(callback: UpdateCallback): void

// 应用代码
import { pasteboard } from '@kit.BasicServicesKit';

const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
let listener = () => {
  console.info('The system pasteboard has changed.');
};
systemPasteboard.onUpdate(listener);
```
