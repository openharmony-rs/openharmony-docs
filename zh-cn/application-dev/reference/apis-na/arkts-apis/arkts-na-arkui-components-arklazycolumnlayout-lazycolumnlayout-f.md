# LazyColumnLayout

## 导入模块

```TypeScript
```

## LazyColumnLayout

```TypeScript
@ComponentBuilder
export declare function LazyColumnLayout(
    content_?: CustomBuilder,
): LazyColumnLayoutAttribute
```

定义LazyColumnLayout组件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function LazyColumnLayout(    content_?: CustomBuilder,): LazyColumnLayoutAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function LazyColumnLayout(    content_?: CustomBuilder,): LazyColumnLayoutAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LazyColumnLayoutAttribute](../../apis-arkui/arkts-apis/arkts-arkui-arkui-components-arklazycolumnlayout-lazycolumnlayoutattribute-c.md) | 懒加载列布局的属性 |


## LazyColumnLayout

```TypeScript
@Builder
export declare function LazyColumnLayout(
    style_: CustomBuilderT<LazyColumnLayoutAttribute>,
    content_?: CustomBuilder
): LazyColumnLayoutAttribute
```

定义LazyColumnLayout组件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function LazyColumnLayout(    style_: CustomBuilderT<LazyColumnLayoutAttribute>,    content_?: CustomBuilder): LazyColumnLayoutAttribute--><!--Device-unnamed-@Builderexport declare function LazyColumnLayout(    style_: CustomBuilderT<LazyColumnLayoutAttribute>,    content_?: CustomBuilder): LazyColumnLayoutAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style_ | CustomBuilderT&lt;[LazyColumnLayoutAttribute](../../apis-arkui/arkts-apis/arkts-arkui-arkui-components-arklazycolumnlayout-lazycolumnlayoutattribute-c.md)&gt; | 是 | The style to create a LazyColumnLayout. |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LazyColumnLayoutAttribute](../../apis-arkui/arkts-apis/arkts-arkui-arkui-components-arklazycolumnlayout-lazycolumnlayoutattribute-c.md) | LazyColumnLayout的属性。 |

