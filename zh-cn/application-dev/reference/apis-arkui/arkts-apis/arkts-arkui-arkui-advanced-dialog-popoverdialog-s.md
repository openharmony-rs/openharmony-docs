# PopoverDialog

跟手弹出框，基于目标组件位置弹出，上述的TipsDialog、SelectDialog、ConfirmDialog、AlertDialog、LoadingDialog、CustomContentDialog都可作为弹出框内容。

**起始版本：** 14

**装饰器类型：** @Component

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AlertDialog, ButtonOptions, ConfirmDialog, LoadingDialog, SelectDialog, TipsDialog, CustomContentDialog, PopoverDialog, PopoverOptions } from '@kit.ArkUI';
```

## popover

```TypeScript
popover: PopoverOptions
```

配置跟手弹出框的参数，包含弹出框内容、位置等属性，具体参见PopoverOptions类型说明。

**类型：** [PopoverOptions](arkts-arkui-arkui-advanced-dialog-popoveroptions-i.md)

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## targetBuilder

```TypeScript
targetBuilder: Callback<void>
```

跟手弹出框基于的目标组件构建器函数，用于定义弹出框显示的参考位置组件。

**类型：** Callback&lt;void&gt;

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## visible

```TypeScript
visible: boolean
```

是否显示跟手弹出框。true表示显示弹出框，false表示隐藏弹出框。

默认值为false，隐藏弹出框。

**类型：** boolean

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
