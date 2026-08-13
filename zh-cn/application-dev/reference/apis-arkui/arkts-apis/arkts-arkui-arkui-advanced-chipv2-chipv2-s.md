# ChipV2

ChipV2是提供丰富样式和交互能力的操作块组件，支持前缀图标、后缀图标、激活状态、关闭按钮等特性，支持Symbol和Image两种图标类型，并提供完善的无障碍访问能力。该组件适用于搜索历史记录、邮件发送列表、标签选择、过滤器、联系人 展示等场景。 该组件基于[状态管理（V2）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)实现，相较于 [状态管理（V1）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，状态管理（V2）增强了对数据对象的深度观察与管理能力，不再局限于组 件层级。借助状态管理（V2），开发者可以更灵活地控制组件的数据和状态，实现更高效的用户界面刷新。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare struct ChipV2--><!--Device-unnamed-export declare struct ChipV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## build

```TypeScript
build(): void
```

build函数用于构造ChipV2高级组件的UI结构。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2-build(): void--><!--Device-ChipV2-build(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## chipV2Options

```TypeScript
@Require
  @Param
  readonly chipV2Options: ChipV2Options
```

定义ChipV2组件的参数，用于自定义ChipV2组件的外观和行为，包含label、prefixIcon、suffixIcon、allowClose、activated、backgroundColor、size等配置项。

**类型：** [ChipV2Options](../../apis-na/arkts-apis/arkts-na-arkui-advanced-chipv2-chipv2options-c.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2-@Require  @Param  readonly chipV2Options: ChipV2Options--><!--Device-ChipV2-@Require  @Param  readonly chipV2Options: ChipV2Options-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

