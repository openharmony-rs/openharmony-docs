# IConsumeDecoratedVariable

Define Consume decoration variable interface.

**继承/实现关系：** IConsumeDecoratedVariable extends IDecoratedMutableVariable<T>, IDecoratedV1Variable<T>

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface IConsumeDecoratedVariable--><!--Device-unnamed-export declare interface IConsumeDecoratedVariable-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## resetOnReuse

```TypeScript
resetOnReuse(provideAlias: string, watchFunc?: WatchFuncType, consumeOptions?: ConsumeOptions<T>): void
```

当@Reusable Component实例被重用时，重置Consume变量。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IConsumeDecoratedVariable-resetOnReuse(provideAlias: string, watchFunc?: WatchFuncType, consumeOptions?: ConsumeOptions<T>): void--><!--Device-IConsumeDecoratedVariable-resetOnReuse(provideAlias: string, watchFunc?: WatchFuncType, consumeOptions?: ConsumeOptions<T>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| provideAlias | string | 是 | 同名 |
| watchFunc | [WatchFuncType](arkts-na-watchfunctype-t.md) | 否 | watch函数类型 |
| consumeOptions | [ConsumeOptions](arkts-na-decorator-consumeoptions-i.md)&lt;T&gt; | 否 | 具有默认值的选项 |

