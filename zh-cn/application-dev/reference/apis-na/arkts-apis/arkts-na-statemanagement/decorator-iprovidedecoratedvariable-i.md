# IProvideDecoratedVariable

Define Provide decoration variable interface.

**继承/实现关系：** IProvideDecoratedVariable extends [IDecoratedMutableVariable<T>](IDecoratedMutableVariable<T>), [IDecoratedV1Variable<T>](IDecoratedV1Variable<T>)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface IProvideDecoratedVariable<T> extends IDecoratedMutableVariable<T>, IDecoratedV1Variable<T>--><!--Device-unnamed-export declare interface IProvideDecoratedVariable<T> extends IDecoratedMutableVariable<T>, IDecoratedV1Variable<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## resetOnReuse

```TypeScript
resetOnReuse(newValue: T): void
```

在重用@Reusable Component实例时提供Link变量。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IProvideDecoratedVariable-resetOnReuse(newValue: T): void--><!--Device-IProvideDecoratedVariable-resetOnReuse(newValue: T): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newValue | T | 是 | 默认值 |

