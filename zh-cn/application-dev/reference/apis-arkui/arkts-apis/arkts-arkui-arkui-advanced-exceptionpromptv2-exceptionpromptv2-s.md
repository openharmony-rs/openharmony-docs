# ExceptionPromptV2

异常提示V2组件，适用于有异常需要提示异常内容的情况。 该组件基于\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_实现，相较于 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_，状态管理（V2）增强了对数据对象的深度观察与管理能力，不再局限于组 件层级。借助状态管理（V2），开发者可以通过该组件更灵活地控制异常提示的数据和状态，实现更高效的用户界面刷新。 > **说明：** > > - 该组件仅可在Stage模型下使用。 > > - 如果ExceptionPromptV2设置[通用属性]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_和 > [通用事件]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_，编译工具链会额外生成节点\_\_Common\_\_，并将通用属性或通用事件挂载在\_\_Common\_\_上，而不是直接应用到 > ExceptionPromptV2本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议ExceptionPromptV2设置通用属性和通用事件。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**装饰器类型：** @ComponentV2

<!--Device-unnamed-export declare struct ExceptionPromptV2--><!--Device-unnamed-export declare struct ExceptionPromptV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onActionTextClick

```TypeScript
onActionTextClick?: OnActionTextClickCallback
```

点击右侧图标按钮的回调函数。缺省时不执行任何操作。

**类型：** OnActionTextClickCallback

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ExceptionPromptV2-onActionTextClick?: OnActionTextClickCallback--><!--Device-ExceptionPromptV2-onActionTextClick?: OnActionTextClickCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onTipClick

```TypeScript
onTipClick?: OnTipClickCallback
```

点击左侧提示文本的回调函数，缺省时不执行任何操作。

**类型：** OnTipClickCallback

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ExceptionPromptV2-onTipClick?: OnTipClickCallback--><!--Device-ExceptionPromptV2-onTipClick?: OnTipClickCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options: PromptOptionsV2
```

指定当前异常提示的配置信息。

**类型：** PromptOptionsV2

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ExceptionPromptV2-options: PromptOptionsV2--><!--Device-ExceptionPromptV2-options: PromptOptionsV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

