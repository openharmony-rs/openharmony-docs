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

## void类型已弃用

**规则：** `sdk-limited-void-type`

**规则解释：**

在ArkTS1.1中，`void`已弃用。

**变更原因：**

在ArkTS1.1中，`void`是一个类型。在ArkTS1.2中，`void`不再是类型，它没有实体，只能用作函数、方法和lambda表达式的返回类型，表示不返回任何值。

**适配建议：**

请使用undefined代替。

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