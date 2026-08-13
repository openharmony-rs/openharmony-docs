# TreeViewV2

树视图V2组件。树视图作为一种分层显示的列表，适合显示嵌套结构。拥有父列表项和子列表项，可展开或折叠。 用于效率型应用，如备忘录、电子邮件、图库中的侧边导航栏。 该组件基于[状态管理（V2）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)实现，相较于 [状态管理（V1）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，状态管理（V2）增强了对数据对象的深度观察与管理能力，不再局限于组 件层级。借助状态管理（V2），开发者可以通过该组件更灵活地控制树视图的数据和状态，实现更高效的用户界面刷新。 > **说明：** > > - 如果TreeViewV2设置通用属性和通用事件，编译工具链 > 会额外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到TreeViewV2本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议TreeViewV2设置通用 > 属性和通用事件。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare struct TreeViewV2--><!--Device-unnamed-export declare struct TreeViewV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## build

```TypeScript
@Builder
  build(): void
```

构建组件的方法。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TreeViewV2-@Builder  build(): void--><!--Device-TreeViewV2-@Builder  build(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## treeControllerV2

```TypeScript
@Param
  treeControllerV2: TreeControllerV2
```

树视图节点控制器。

**类型：** [TreeControllerV2](arkts-na-arkui-advanced-treeviewv2-treecontrollerv2-c.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TreeViewV2-@Param  treeControllerV2: TreeControllerV2--><!--Device-TreeViewV2-@Param  treeControllerV2: TreeControllerV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

