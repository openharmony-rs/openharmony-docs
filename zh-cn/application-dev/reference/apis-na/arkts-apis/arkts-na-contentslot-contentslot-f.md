# ContentSlot

## ContentSlot

```TypeScript
@ComponentBuilder
export declare function ContentSlot(
    content: Content
): ContentSlotAttribute
```

当内容添加到占位符组件时调用。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function ContentSlot(    content: Content): ContentSlotAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function ContentSlot(    content: Content): ContentSlotAttribute-End-->

**系统能力：** 
- SystemCapability.ArkUI.ArkUI.Full
- SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | Content | 是 | Content作为ContentSlot的管理器，通过Native侧提供的接口，可以注册并触发ContentSlot的上下树事件回调以及管理ContentSlot的子组件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ContentSlotAttribute |  |


## ContentSlot

```TypeScript
@Builder
export declare function ContentSlot(
    style: CustomBuilderT<ContentSlotAttribute>
): ContentSlotAttribute
```

定义ContentSlot组件。需要在组件属性设置开始时调用setContentSlotOptions，并在组件属性设置结束时调用applyAttributeFinish。

**起始版本：** 26.1.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.1.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function ContentSlot(    style: CustomBuilderT<ContentSlotAttribute>): ContentSlotAttribute--><!--Device-unnamed-@Builderexport declare function ContentSlot(    style: CustomBuilderT<ContentSlotAttribute>): ContentSlotAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;ContentSlotAttribute&gt; | 是 | 用于设置ContentSlot属性的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ContentSlotAttribute | ContentSlot属性对象。 |

