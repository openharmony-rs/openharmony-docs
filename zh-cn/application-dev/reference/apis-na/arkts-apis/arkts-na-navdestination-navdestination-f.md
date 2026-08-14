# NavDestination

## NavDestination

```TypeScript
@ComponentBuilder
export declare function NavDestination(

  content_?: CustomBuilder
): NavDestinationAttribute
```

创建Navigation子页面的根容器。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function NavDestination(  content_?: CustomBuilder): NavDestinationAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function NavDestination(  content_?: CustomBuilder): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content_ | CustomBuilder | 否 | 支持多个子组件。&lt;br/&gt;**说明：** &lt;br/&gt;子组件类型：系统组件和自定义组件，支持渲染控制类型（ [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、 [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)和 [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NavDestinationAttribute](arkts-na-navdestination-navdestinationattribute-i.md) |  |


## NavDestination

```TypeScript
@Builder
export declare function NavDestination(
 style_: CustomBuilderT<NavDestinationAttribute>,
 content_?: CustomBuilder,
): NavDestinationAttribute
```

定义NavDestination组件

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function NavDestination( style_: CustomBuilderT<NavDestinationAttribute>, content_?: CustomBuilder,): NavDestinationAttribute--><!--Device-unnamed-@Builderexport declare function NavDestination( style_: CustomBuilderT<NavDestinationAttribute>, content_?: CustomBuilder,): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style_ | CustomBuilderT&lt;[NavDestinationAttribute](arkts-na-navdestination-navdestinationattribute-i.md)&gt; | 是 | navDestination属性实例 |
| content_ | CustomBuilder | 否 | 内容区 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NavDestinationAttribute](arkts-na-navdestination-navdestinationattribute-i.md) |  |

