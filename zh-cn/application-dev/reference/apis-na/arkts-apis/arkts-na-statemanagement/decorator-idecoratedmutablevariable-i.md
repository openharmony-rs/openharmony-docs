# IDecoratedMutableVariable

定义可读写状态变量接口

**继承/实现关系：** IDecoratedMutableVariable extends [IDecoratedReadableVariable<T>](IDecoratedReadableVariable<T>)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface IDecoratedMutableVariable<T> extends IDecoratedReadableVariable<T>--><!--Device-unnamed-export declare interface IDecoratedMutableVariable<T> extends IDecoratedReadableVariable<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## set

```TypeScript
set(newValue: T): void
```

Set the state variable with a new Value.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IDecoratedMutableVariable-set(newValue: T): void--><!--Device-IDecoratedMutableVariable-set(newValue: T): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newValue | T | 是 |  |

