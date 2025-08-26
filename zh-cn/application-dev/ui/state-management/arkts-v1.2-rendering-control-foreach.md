# ArkTS1.2 ForEach组件迁移规范

本指南介绍ArkTS1.2语言中ForEach组件的功能变更和迁移规范。

> **说明：**
>
> 从API version 20起引入ArkTS1.2。

## 迁移说明

ArkTS1.2需要加入模块导入语句：

```ts
import { ForEach } from '@ohos.arkui.component';
```

## 类型一致性校验

ArkTS1.1 ForEach允许的写法：

```ts
arr: Array<Type1 | Type2> = [];

ForEach(this.arr, (item: Type1) => {...}, (item: Type2) => item.toString()) // 只使用一种类型
```

ArkTS1.2 ForEach的API声明：

```ts
ForEach<T>(
  arr: Array<T>,
  itemGenerator: (item: T, index: number) => void,
  keyGenerator?: (item: T, index: number) => string
): ForEachAttribute
```

在ArkTS1.2中，ForEach数组类型需要与itemGenerator、keyGenerator的参数item的类型保持一致，否则会报编译错误。

正确写法：

```ts
arr: Array<Type1 | Type2> = [];

ForEach(this.arr, (item: Type1 | Type2) => {...}, (item: Type1 | Type2) => item.toString()) // 类型保持一致
```
