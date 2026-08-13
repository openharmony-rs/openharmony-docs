# TabContent

## TabContent

```TypeScript
@ComponentBuilder
export declare function TabContent(
    
    content_?: CustomBuilder,
): TabContentAttribute
```

创建支持单个子组件。&lt;br/&gt;**说明：**&lt;br/&gt;可内置系统组件和自定义组件，支持渲染控制类型（ [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、 [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)和 [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)）。页签和内容。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function TabContent(        content_?: CustomBuilder,): TabContentAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function TabContent(        content_?: CustomBuilder,): TabContentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content_ | CustomBuilder | 否 | 支持单个子组件。&lt;br/&gt;**说明：**&lt;br/&gt;可内置系统组件和自定义组件，支持渲染控制类型（ [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、 [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)和 [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| TabContentAttribute |  |


## TabContent

```TypeScript
@Builder
export declare function TabContent(
 style_: CustomBuilderT<TabContentAttribute>,
 content_?: CustomBuilder,
): TabContentAttribute
```

定义选项卡内容组件

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function TabContent( style_: CustomBuilderT<TabContentAttribute>, content_?: CustomBuilder,): TabContentAttribute--><!--Device-unnamed-@Builderexport declare function TabContent( style_: CustomBuilderT<TabContentAttribute>, content_?: CustomBuilder,): TabContentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style_ | CustomBuilderT&lt;TabContentAttribute&gt; | 是 | tabContent属性实例 |
| content_ | CustomBuilder | 否 | 选项卡内容 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| TabContentAttribute |  |

