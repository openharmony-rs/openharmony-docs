# PopoverDialogV2

跟手弹出框，基于目标组件位置弹出，上文中的TipsDialogV2、SelectDialogV2、ConfirmDialogV2、AlertDialogV2、LoadingDialogV2、CustomContentDialogV2都可作为弹出框内容。

**起始版本：** 18

**装饰器类型：** @ComponentV2

<!--Device-unnamed-export declare struct PopoverDialogV2--><!--Device-unnamed-export declare struct PopoverDialogV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AdvancedDialogV2OnCheckedChange, LoadingDialogV2, AdvancedDialogV2Button, AdvancedDialogV2ButtonAction, AlertDialogV2, CustomContentDialogV2, PopoverDialogV2Options, PopoverDialogV2, SelectDialogV2, PopoverDialogV2OnVisibleChange, TipsDialogV2, AdvancedDialogV2ButtonOptions, ConfirmDialogV2 } from '@kit.ArkUI';
```

## $visible

```TypeScript
$visible?: PopoverDialogV2OnVisibleChange
```

修改跟手弹出框的显示状态时触发的回调函数，建议在visible后使用!!语法设置双向同步。

默认无事件。

**类型：** PopoverDialogV2OnVisibleChange

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopoverDialogV2-$visible?: PopoverDialogV2OnVisibleChange--><!--Device-PopoverDialogV2-$visible?: PopoverDialogV2OnVisibleChange-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## popover

```TypeScript
popover: PopoverDialogV2Options
```

配置跟手弹出框的参数。

**类型：** PopoverDialogV2Options

**起始版本：** 18

**装饰器类型：** @Require、@Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopoverDialogV2-popover: PopoverDialogV2Options--><!--Device-PopoverDialogV2-popover: PopoverDialogV2Options-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## targetBuilder

```TypeScript
targetBuilder: CustomBuilder
```

跟手弹出框基于的目标组件。

**类型：** CustomBuilder

**起始版本：** 18

**装饰器类型：** @BuilderParam

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopoverDialogV2-targetBuilder: CustomBuilder--><!--Device-PopoverDialogV2-targetBuilder: CustomBuilder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## visible

```TypeScript
visible: boolean
```

跟手弹出框的显示状态。

值为true时跟手弹出框显示，为false时隐藏。

**类型：** boolean

**起始版本：** 18

**装饰器类型：** @Require、@Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopoverDialogV2-visible: boolean--><!--Device-PopoverDialogV2-visible: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

