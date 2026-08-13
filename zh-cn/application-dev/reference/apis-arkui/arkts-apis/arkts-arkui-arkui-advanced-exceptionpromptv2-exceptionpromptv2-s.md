# ExceptionPromptV2

异常提示V2组件，适用于有异常需要提示异常内容的情况。 该组件基于[状态管理（V2）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)实现，相较于 [状态管理（V1）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，状态管理（V2）增强了对数据对象的深度观察与管理能力，不再局限于组 件层级。借助状态管理（V2），开发者可以通过该组件更灵活地控制异常提示的数据和状态，实现更高效的用户界面刷新。 > **说明：** > > - 该组件仅可在Stage模型下使用。 > > - 如果ExceptionPromptV2设置通用属性和 > 通用事件，编译工具链会额外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到 > ExceptionPromptV2本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议ExceptionPromptV2设置通用属性和通用事件。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare struct ExceptionPromptV2--><!--Device-unnamed-export declare struct ExceptionPromptV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onActionTextClick

```TypeScript
@Event
  onActionTextClick?: OnActionTextClickCallback
```

点击右侧图标按钮的回调函数。缺省时不执行任何操作。

**类型：** [OnActionTextClickCallback](arkts-arkui-onactiontextclickcallback-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ExceptionPromptV2-@Event  onActionTextClick?: OnActionTextClickCallback--><!--Device-ExceptionPromptV2-@Event  onActionTextClick?: OnActionTextClickCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onTipClick

```TypeScript
@Event
  onTipClick?: OnTipClickCallback
```

点击左侧提示文本的回调函数，缺省时不执行任何操作。

**类型：** [OnTipClickCallback](arkts-arkui-ontipclickcallback-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ExceptionPromptV2-@Event  onTipClick?: OnTipClickCallback--><!--Device-ExceptionPromptV2-@Event  onTipClick?: OnTipClickCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
@Param
  options: PromptOptionsV2
```

指定当前异常提示的配置信息。

**类型：** [PromptOptionsV2](arkts-arkui-arkui-advanced-exceptionpromptv2-promptoptionsv2-c.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ExceptionPromptV2-@Param  options: PromptOptionsV2--><!--Device-ExceptionPromptV2-@Param  options: PromptOptionsV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

