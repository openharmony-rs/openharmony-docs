# ScrollBar

## ScrollBar

```TypeScript
@ComponentBuilder
export declare function ScrollBar(
    value: ScrollBarOptions, 
    content_?: CustomBuilder,
): ScrollBarAttribute
```

定义滚动条组件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function ScrollBar(    value: ScrollBarOptions,     content_?: CustomBuilder,): ScrollBarAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function ScrollBar(    value: ScrollBarOptions,     content_?: CustomBuilder,): ScrollBarAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ScrollBarOptions](arkts-na-scrollbar-scrollbaroptions-i.md) | 是 |  |
| content_ | CustomBuilder | 否 | 子组件 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ScrollBarAttribute |  |


## ScrollBar

```TypeScript
@Builder
export declare function ScrollBar(
    style_: CustomBuilderT<ScrollBarAttribute>, 
    content_?: CustomBuilder
): ScrollBarAttribute
```

定义滚动条组件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function ScrollBar(    style_: CustomBuilderT<ScrollBarAttribute>,     content_?: CustomBuilder): ScrollBarAttribute--><!--Device-unnamed-@Builderexport declare function ScrollBar(    style_: CustomBuilderT<ScrollBarAttribute>,     content_?: CustomBuilder): ScrollBarAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style_ | CustomBuilderT&lt;ScrollBarAttribute&gt; | 是 | The style to create a ScrollBar. |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ScrollBarAttribute | ScrollBar的属性。 |

