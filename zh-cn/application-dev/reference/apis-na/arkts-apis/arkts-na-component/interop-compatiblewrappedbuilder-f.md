# compatibleWrappedBuilder

## compatibleWrappedBuilder

```TypeScript
export declare function compatibleWrappedBuilder(builder: Any, ...args: FixedArray<ESValue>): void
```

为ArkTS-Sta提供使用ArkTS-Dyn WrappedBuilder对象的互操作方法。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function compatibleWrappedBuilder(builder: Any, ...args: FixedArray<ESValue>): void--><!--Device-unnamed-export declare function compatibleWrappedBuilder(builder: Any, ...args: FixedArray<ESValue>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | Any | 是 | ArkTS-Dyn WrappedBuilder对象。 |
| args | FixedArray&lt;ESValue&gt; | 是 | ArkTS-Dyn WrappedBuilder对象使用时的参数。 |

