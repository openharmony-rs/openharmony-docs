# CustomDialogController

自定义弹窗的控制器。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class CustomDialogController--><!--Device-unnamed-export declare class CustomDialogController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## close

```TypeScript
close(): void
```

关闭显示的自定义弹窗，若已关闭，则不生效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogController-close(): void--><!--Device-CustomDialogController-close(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value: CustomDialogControllerOptions)
```

自定义弹窗的构造器。 > **说明：** > > 自定义弹窗的所有参数，不支持动态刷新，但可以通过设置customStyle为true，并在自定义组件上设置 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_、 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_、 \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_等属性，通过属性绑定的状态变量来实现动态刷新的效果。 > > 在CustomDialogController作为全局变量以实现全局自定义弹窗的场景下，若对controller重新赋值，则无法通过其关闭之前的弹窗。建议在重新赋值前先关闭弹窗。 > > 在自定义弹窗内拉起另一个自定义弹窗时，不建议直接关闭拉起方。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogController-constructor(value: CustomDialogControllerOptions)--><!--Device-CustomDialogController-constructor(value: CustomDialogControllerOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 |  |

## getExternalOptions

```TypeScript
getExternalOptions(): CustomDialogControllerExternalOptions
```

获取自定义弹窗的外部选项。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogController-getExternalOptions(): CustomDialogControllerExternalOptions--><!--Device-CustomDialogController-getExternalOptions(): CustomDialogControllerExternalOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回自定义弹窗的外部选项。 |

## getState

```TypeScript
getState(): PromptActionCommonState
```

获取自定义弹窗的状态。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogController-getState(): PromptActionCommonState--><!--Device-CustomDialogController-getState(): PromptActionCommonState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回对应的弹窗状态。 |

## open

```TypeScript
open(): void
```

显示自定义弹窗内容，允许多次使用。如果弹框为SubWindow模式，弹窗可以显示在主窗口之外，此时弹框不允许再弹出SubWindow弹框。 > **说明：** > > 不支持在输入法类型窗口中使用子窗（showInSubwindow为true）的CustomDialog，详情见输入法框架的约束与限制说明 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogController-open(): void--><!--Device-CustomDialogController-open(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

