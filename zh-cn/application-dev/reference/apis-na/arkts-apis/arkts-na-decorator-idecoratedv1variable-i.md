# IDecoratedV1Variable

Define V1 decorated variable interface.

**继承/实现关系：** IDecoratedV1Variable extends [IDecoratedVariable](arkts-na-decorator-idecoratedvariable-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface IDecoratedV1Variable--><!--Device-unnamed-export declare interface IDecoratedV1Variable-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## registerWatchToSource

```TypeScript
registerWatchToSource(decoratedVar: IDecoratedV1Variable<T>): void
```

Registers the watch callback function with the data source.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IDecoratedV1Variable-registerWatchToSource(decoratedVar: IDecoratedV1Variable<T>): void--><!--Device-IDecoratedV1Variable-registerWatchToSource(decoratedVar: IDecoratedV1Variable<T>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| decoratedVar | [IDecoratedV1Variable](arkts-na-decorator-idecoratedv1variable-i.md)&lt;T&gt; | 是 |  |

