# IObjectLinkDecoratedVariable

Define ObjectLink decoration variable interface.

**继承/实现关系：** IObjectLinkDecoratedVariable extends IDecoratedImmutableVariable<T>, IDecoratedUpdatableVariable<T>, IDecoratedV1Variable<T>

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface IObjectLinkDecoratedVariable--><!--Device-unnamed-export declare interface IObjectLinkDecoratedVariable-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## resetOnReuse

```TypeScript
resetOnReuse(newValue: T): void
```

当@可重用组件实例时，重置ObjectLink变量。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IObjectLinkDecoratedVariable-resetOnReuse(newValue: T): void--><!--Device-IObjectLinkDecoratedVariable-resetOnReuse(newValue: T): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newValue | T | 是 | 默认值 |

