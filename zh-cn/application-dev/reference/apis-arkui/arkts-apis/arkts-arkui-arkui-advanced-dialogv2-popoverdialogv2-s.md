# PopoverDialogV2

跟手弹出框，基于目标组件位置弹出，上述的TipsDialogV2、SelectDialogV2、ConfirmDialogV2、AlertDialogV2、 LoadingDialogV2、CustomContentDialogV2都可作为弹出框内容。适用于需要跟随目标组件位置显示的场景，如工具提示、操作引导等。

**起始版本：** 18

<!--Device-unnamed-export declare struct PopoverDialogV2--><!--Device-unnamed-export declare struct PopoverDialogV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AlertDialogV2, AdvancedDialogV2Button, AdvancedDialogV2ButtonOptions, AdvancedDialogV2ButtonAction, AdvancedDialogV2OnCheckedChange, ConfirmDialogV2, LoadingDialogV2, SelectDialogV2, TipsDialogV2, CustomContentDialogV2, PopoverDialogV2, PopoverDialogV2OnVisibleChange, PopoverDialogV2Options } from '@kit.ArkUI';
```

## $visible

```TypeScript
@Event
  $visible?: PopoverDialogV2OnVisibleChange
```

修改跟手弹出框的显示状态时触发的回调函数，建议在visible后使用!!语法（如`visible: this.isShow!!`）设置双向同步，当弹出框内部改变显示状态时会同步更新外部变量。 默认无事件。

**类型：** [PopoverDialogV2OnVisibleChange](arkts-arkui-popoverdialogv2onvisiblechange-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopoverDialogV2-@Event  $visible?: PopoverDialogV2OnVisibleChange--><!--Device-PopoverDialogV2-@Event  $visible?: PopoverDialogV2OnVisibleChange-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## popover

```TypeScript
@Require
  @Param
  popover: PopoverDialogV2Options
```

配置跟手弹出框的参数。

**类型：** [PopoverDialogV2Options](arkts-arkui-arkui-advanced-dialogv2-popoverdialogv2options-i.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopoverDialogV2-@Require  @Param  popover: PopoverDialogV2Options--><!--Device-PopoverDialogV2-@Require  @Param  popover: PopoverDialogV2Options-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## targetBuilder

```TypeScript
@BuilderParam
  targetBuilder: CustomBuilder
```

跟手弹出框基于的目标组件。

**类型：** CustomBuilder

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopoverDialogV2-@BuilderParam  targetBuilder: CustomBuilder--><!--Device-PopoverDialogV2-@BuilderParam  targetBuilder: CustomBuilder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## visible

```TypeScript
@Require
  @Param
  visible: boolean
```

跟手弹出框的显示状态。 值为true时跟手弹出框显示，为false时隐藏。

**类型：** boolean

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopoverDialogV2-@Require  @Param  visible: boolean--><!--Device-PopoverDialogV2-@Require  @Param  visible: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

