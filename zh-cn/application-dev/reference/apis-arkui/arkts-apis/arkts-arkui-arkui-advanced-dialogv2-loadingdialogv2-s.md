# LoadingDialogV2

进度加载类弹出框，操作正在执行时的提示信息。适用于耗时操作的场景，如数据加载、文件上传等，用于告知用户当前正在处理中。

**起始版本：** 18

<!--Device-unnamed-export declare struct LoadingDialogV2--><!--Device-unnamed-export declare struct LoadingDialogV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AlertDialogV2, AdvancedDialogV2Button, AdvancedDialogV2ButtonOptions, AdvancedDialogV2ButtonAction, AdvancedDialogV2OnCheckedChange, ConfirmDialogV2, LoadingDialogV2, SelectDialogV2, TipsDialogV2, CustomContentDialogV2, PopoverDialogV2, PopoverDialogV2OnVisibleChange, PopoverDialogV2Options } from '@kit.ArkUI';
```

## content

```TypeScript
@Param
  content?: ResourceStr
```

加载弹出框内容。 默认为空。 **说明：** 内容超过十行会显示“...”。

**类型：** ResourceStr

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-LoadingDialogV2-@Param  content?: ResourceStr--><!--Device-LoadingDialogV2-@Param  content?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

