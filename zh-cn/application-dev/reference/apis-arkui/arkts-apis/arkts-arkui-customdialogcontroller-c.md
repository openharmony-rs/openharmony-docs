# CustomDialogController

自定义弹窗的控制器。

## 导入对象

```ts
dialogController : CustomDialogController | null = new CustomDialogController(CustomDialogControllerOptions)
```

> **说明：**  
>  
> - CustomDialogController仅在作为@CustomDialog和@Component struct成员变量，且在@Component struct内部定义时赋值才有效，具体用法可参考下方示例。  
>  
> - 若尝试在CustomDialog中传入多个其他的Controller，以实现在CustomDialog中打开另一个或另一些CustomDialog，那么此处需要将指向自己的controller放在所有controller的后  
> 面。详细用法可参考[示例1（弹出嵌套弹窗）](docroot://reference/apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md#示例1弹出嵌套弹窗)。

**起始版本：** 7

<!--Device-unnamed-declare class CustomDialogController--><!--Device-unnamed-declare class CustomDialogController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="close"></a>
## close

```TypeScript
close()
```

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogController-close()--><!--Device-CustomDialogController-close()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="constructor"></a>
## constructor

```TypeScript
constructor(value: CustomDialogControllerOptions)
```

自定义弹窗的构造器。

> **说明：**  
>  
> 自定义弹窗的所有参数，不支持动态刷新，但可以通过设置customStyle为true，并在自定义组件上设置背景色  
> [backgroundColor](../arkts-components/arkts-arkui-commonmethod-c.md#backgroundcolor-1)、背景模糊  
> [backgroundBlurStyle](../arkts-components/arkts-arkui-commonmethod-c.md#backgroundblurstyle-1)  
> 、[尺寸设置](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)等属性，通过属性绑定的状态变量来实现动态刷新的效果。  
>  
> 在CustomDialogController作为全局变量以实现全局自定义弹窗的场景下，若对controller重新赋值，则无法通过其关闭之前的弹窗。建议在重新赋值前先关闭弹窗。  
>  
> 在自定义弹窗内拉起另一个自定义弹窗时，不建议直接关闭拉起方。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogController-constructor(value: CustomDialogControllerOptions)--><!--Device-CustomDialogController-constructor(value: CustomDialogControllerOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CustomDialogControllerOptions](arkts-arkui-customdialogcontrolleroptions-i.md) | 是 | 配置自定义弹窗的参数。 |

<a id="getstate"></a>
## getState

```TypeScript
getState(): PromptActionCommonState
```

获取自定义弹窗的状态。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogController-getState(): PromptActionCommonState--><!--Device-CustomDialogController-getState(): PromptActionCommonState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PromptActionCommonState](arkts-arkui-promptactioncommonstate-t.md) | 返回对应的弹窗状态。 |

<a id="open"></a>
## open

```TypeScript
open()
```

显示自定义弹窗内容，允许多次使用，但如果弹框为SubWindow模式，则该弹框不允许再弹出SubWindow弹框。

> **说明：**  
>  
> 不支持在输入法类型窗口中使用子窗（showInSubwindow为true）的CustomDialog，详情见输入法框架的约束与限制说明  
> [createPanel](../../apis-ime-kit/arkts-apis/arkts-ime-inputmethodengine-inputmethodability-i.md#createpanel-1)  
> 。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogController-open()--><!--Device-CustomDialogController-open()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

