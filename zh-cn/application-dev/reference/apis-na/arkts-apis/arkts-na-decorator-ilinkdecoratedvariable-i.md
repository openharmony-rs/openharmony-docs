# ILinkDecoratedVariable

Define Link decoration variable interface.

**继承/实现关系：** ILinkDecoratedVariable extends IDecoratedMutableVariable<T>, IDecoratedV1Variable<T>

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface ILinkDecoratedVariable--><!--Device-unnamed-export declare interface ILinkDecoratedVariable-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## resetOnReuse

```TypeScript
resetOnReuse(newValue: LinkSourceType<T>): void
```

在重用@可重用组件实例时重置链接变量。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ILinkDecoratedVariable-resetOnReuse(newValue: LinkSourceType<T>): void--><!--Device-ILinkDecoratedVariable-resetOnReuse(newValue: LinkSourceType<T>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newValue | [LinkSourceType](arkts-na-linksourcetype-t.md)&lt;T&gt; | 是 | 默认值 |

