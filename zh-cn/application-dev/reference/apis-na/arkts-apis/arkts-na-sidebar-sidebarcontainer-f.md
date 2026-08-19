# SideBarContainer

## SideBarContainer

```TypeScript
@ComponentBuilder
export declare function SideBarContainer(
  type?: SideBarContainerType,
  content_?: CustomBuilder
): SideBarContainerAttribute
```

创建侧边栏容器。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function SideBarContainer(  type?: SideBarContainerType,  content_?: CustomBuilder): SideBarContainerAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function SideBarContainer(  type?: SideBarContainerType,  content_?: CustomBuilder): SideBarContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [SideBarContainerType](arkts-na-sidebar-sidebarcontainertype-e.md) | 否 | 设置侧边栏的显示类型。<br/>默认值：SideBarContainerType.Embed |
| content_ | CustomBuilder | 否 | 可以包含子组件。<br/>**说明：** <br/>1. 子组件类型：系统组件和自定义组件，不支持渲染控制类型（ [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、 [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)和 [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)）。<br/>2. 子组件个数：必须且仅包含2个子组件。&lt; br/&gt;3. 子组件个数异常时：3个或以上子组件，显示第一个和第二个。1个子组件，显示侧边栏，内容区为空白。<br/>4. SideBarContainer走焦时，先在内容区走焦，再在侧边栏走焦。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SideBarContainerAttribute](arkts-na-sidebar-sidebarcontainerattribute-i.md) |  |


## SideBarContainer

```TypeScript
@Builder
export declare function SideBarContainer(
 	style_: CustomBuilderT<SideBarContainerAttribute>,
 	content_?: CustomBuilder,
): SideBarContainerAttribute
```

定义侧边栏组件

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function SideBarContainer( 	style_: CustomBuilderT<SideBarContainerAttribute>, 	content_?: CustomBuilder,): SideBarContainerAttribute--><!--Device-unnamed-@Builderexport declare function SideBarContainer( 	style_: CustomBuilderT<SideBarContainerAttribute>, 	content_?: CustomBuilder,): SideBarContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style_ | CustomBuilderT&lt;[SideBarContainerAttribute](arkts-na-sidebar-sidebarcontainerattribute-i.md)&gt; | 是 | 侧边栏属性实例 |
| content_ | CustomBuilder | 否 | 内容区 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SideBarContainerAttribute](arkts-na-sidebar-sidebarcontainerattribute-i.md) |  |

