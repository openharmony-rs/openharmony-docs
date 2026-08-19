# Scroll

## Scroll

```TypeScript
@ComponentBuilder
export declare function Scroll(
    scroller?: Scroller, 
    content_?: CustomBuilder,
): ScrollAttribute
```

创建Scroll滚动容器。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Scroll(    scroller?: Scroller,     content_?: CustomBuilder,): ScrollAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Scroll(    scroller?: Scroller,     content_?: CustomBuilder,): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scroller | [Scroller](arkts-na-scroll-scroller-c.md) | 否 |  |
| content_ | CustomBuilder | 否 | 子组件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ScrollAttribute |  |


## Scroll

```TypeScript
@Builder
export declare function Scroll(
    style_: CustomBuilderT<ScrollAttribute>, 
    content_?: CustomBuilder
): ScrollAttribute
```

定义滚动组件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function Scroll(    style_: CustomBuilderT<ScrollAttribute>,     content_?: CustomBuilder): ScrollAttribute--><!--Device-unnamed-@Builderexport declare function Scroll(    style_: CustomBuilderT<ScrollAttribute>,     content_?: CustomBuilder): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style_ | CustomBuilderT&lt;ScrollAttribute&gt; | 是 | 创建滚动的样式 |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ScrollAttribute | Scroll的属性。 |

