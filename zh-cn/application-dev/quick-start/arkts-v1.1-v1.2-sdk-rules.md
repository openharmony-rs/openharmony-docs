# ArkTS1.2SDK迁移规则

## 可选方法已弃用

**规则：** `optional-methods-deprecated`

**级别：** error

请使用可选属性替代可选方法。

**ArkTS1.1**
```typescript
// ArkTS1.1API定义
interface NativeMediaPlayerBridge {
  resumePlayer?(): void
}

// ArkTS1.1应用代码
import NativeMediaPlayerBridge from 'xxx'
class MediaPlayer implements NativeMediaPlayerBridge {
  resumePlayer(): void { // 错误
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
    resumePlayer?: ResumePlayerFn;
    // 或者resumePlayer: ResumePlayerFn | undefined;
    constructor(resumePlayer?: ResumePlayerFn) {
         this.resumePlayer = resumePlayer;
    }
}
let defaultResumePlayer: ResumePlayerFn = () => {}
const player1 = new MediaPlayer(defaultResumePlayer);
```

## void类型已弃用

**规则：** `void-type-deprecated`

**级别：** error

ArkTS1.2中void类型已弃用，请用undefined代替。
 
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

## API路径已更改

**规则：** `api-path-changed`

**级别：** error

在ArkTS1.2中，所有对象不再作为全局对象，而是置于各自的模块中。开发者需通过import语句引入后使用。

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

## 不必要类型参数

**规则：** `unnecessary-type-argument`

**级别：** error

ArkTS1.2中，`attributeValue`方法不再需要传入泛型参数。

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

## 带引号的连字符属性已弃用

**规则：** `quoted-hyphen-props-deprecated`

**级别：** error

在ArkTS1.2中，对象的属性名称必须是有效标识符，不支持使用单引号和连字符。当属性值为字符串或数字时，应将其名称修改为小驼峰格式。

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

**规则：** `constructor-types-deprecated`

**级别：** error

ArkTS1.2不支持构造函数类型，需要将使用构造函数类型的地方改为lambda函数。

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
const userQuery = new DatabaseQuery<User>(createInstence());
```