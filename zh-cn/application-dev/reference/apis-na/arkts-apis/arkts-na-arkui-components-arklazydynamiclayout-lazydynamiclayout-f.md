# LazyDynamicLayout

## 导入模块

```TypeScript
```

## LazyDynamicLayout

```TypeScript
@ComponentBuilder
export declare function LazyDynamicLayout (
    algorithm: LazyLayoutAlgorithm,
    content_: CustomBuilder,
): LazyDynamicLayoutAttribute
```

定义LazyDynamicLayout组件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function LazyDynamicLayout (    algorithm: LazyLayoutAlgorithm,    content_: CustomBuilder,): LazyDynamicLayoutAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function LazyDynamicLayout (    algorithm: LazyLayoutAlgorithm,    content_: CustomBuilder,): LazyDynamicLayoutAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| algorithm | [LazyLayoutAlgorithm](../../apis-arkui/arkts-apis/arkts-arkui-lazylayoutalgorithm-i.md) | 是 | 懒布局算法。 |
| content_ | CustomBuilder | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LazyDynamicLayoutAttribute](../../apis-arkui/arkts-apis/arkts-arkui-arkui-components-arklazydynamiclayout-lazydynamiclayoutattribute-c.md) |  |


## LazyDynamicLayout

```TypeScript
@Builder
export declare function LazyDynamicLayout(
    style_: CustomBuilderT<LazyDynamicLayoutAttribute>,
    content_?: CustomBuilder
): LazyDynamicLayoutAttribute
```

定义LazyDynamicLayout组件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function LazyDynamicLayout(    style_: CustomBuilderT<LazyDynamicLayoutAttribute>,    content_?: CustomBuilder): LazyDynamicLayoutAttribute--><!--Device-unnamed-@Builderexport declare function LazyDynamicLayout(    style_: CustomBuilderT<LazyDynamicLayoutAttribute>,    content_?: CustomBuilder): LazyDynamicLayoutAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style_ | CustomBuilderT&lt;[LazyDynamicLayoutAttribute](../../apis-arkui/arkts-apis/arkts-arkui-arkui-components-arklazydynamiclayout-lazydynamiclayoutattribute-c.md)&gt; | 是 | The style to create a LazyDynamicLayout. |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LazyDynamicLayoutAttribute](../../apis-arkui/arkts-apis/arkts-arkui-arkui-components-arklazydynamiclayout-lazydynamiclayoutattribute-c.md) | LazyDynamicLayout的属性。 |

