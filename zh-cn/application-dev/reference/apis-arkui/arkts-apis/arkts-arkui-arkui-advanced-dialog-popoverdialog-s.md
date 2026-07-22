# PopoverDialog

弹出框是一种模态窗口，用于临时展示用户需关注的信息或待处理的操作，同时保持当前上下文环境。用户必须完成交互才能退出该模式。
> **说明：**  
>  
> - 该组件仅可在Stage模型下使用。  
>  
> - 如果Dialog设置[通用属性](../../apis-arkui/arkts-components/arkts-arkui-common-attribute.md)和[通用事件](../../apis-arkui/arkts-components/arkts-arkui-common-attribute.md)，编译工具链会额外生  
> 成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到Dialog本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议Dialog设置通用属性和通用事件。

**起始版本：** 14

**装饰器类型：** @Component

<!--Device-unnamed-export declare struct PopoverDialog--><!--Device-unnamed-export declare struct PopoverDialog-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AlertDialog, SelectDialog, ButtonOptions, PopoverOptions, TipsDialog, PopoverDialog, LoadingDialog, CustomContentDialog, ConfirmDialog } from '@kit.ArkUI';
```

## popover

```TypeScript
popover: PopoverOptions
```

配置跟手弹出框的参数。

**类型：** PopoverOptions

**起始版本：** 14

**装饰器类型：** @Require、@Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-PopoverDialog-popover: PopoverOptions--><!--Device-PopoverDialog-popover: PopoverOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## targetBuilder

```TypeScript
targetBuilder: Callback<void>
```

跟手弹出框基于的目标组件。

**类型：** Callback&lt;void&gt;

**起始版本：** 14

**装饰器类型：** @Require、@BuilderParam

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-PopoverDialog-targetBuilder: Callback<void>--><!--Device-PopoverDialog-targetBuilder: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## visible

```TypeScript
visible: boolean
```

跟手弹出框显示状态。visible为true时，表示显示弹出框，visible为false时，表示隐藏弹出框。

默认值为false，隐藏弹出框。

**类型：** boolean

**起始版本：** 14

**装饰器类型：** @Link

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-PopoverDialog-visible: boolean--><!--Device-PopoverDialog-visible: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

