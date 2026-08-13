# ExceptionPrompt

异常提示，适用于有异常需要提示异常内容的情况。 > **说明：** > > - 该组件仅可在Stage模型下使用。 > > - 如果ExceptionPrompt设置通用属性和通用事件， > 编译工具链会额外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到ExceptionPrompt本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议 > ExceptionPrompt设置通用属性和通用事件。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-unnamed-export declare struct ExceptionPrompt--><!--Device-unnamed-export declare struct ExceptionPrompt-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## build

```TypeScript
build(): void
```

The build function is a member function that must return an ArkTS component type (Element) to represent the component to be rendered as a user interface.

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ExceptionPrompt-build(): void--><!--Device-ExceptionPrompt-build(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onActionTextClick

```TypeScript
onActionTextClick?: () => void
```

点击右侧图标按钮的回调函数。缺省时不执行任何操作。

**类型：** () =&gt; void

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ExceptionPrompt-onActionTextClick?: () => void--><!--Device-ExceptionPrompt-onActionTextClick?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onTipClick

```TypeScript
onTipClick?: () => void
```

点击左侧提示文本的回调函数，缺省时不执行任何操作。

**类型：** () =&gt; void

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ExceptionPrompt-onTipClick?: () => void--><!--Device-ExceptionPrompt-onTipClick?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
@Prop options: PromptOptions
```

指定当前异常提示的配置信息。

**类型：** [PromptOptions](arkts-arkui-arkui-advanced-exceptionprompt-promptoptions-i.md)

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ExceptionPrompt-@Prop options: PromptOptions--><!--Device-ExceptionPrompt-@Prop options: PromptOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

