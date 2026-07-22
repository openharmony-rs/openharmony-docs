# LoadingDialogV2

进度加载类弹出框，操作正在执行时的提示信息。

**起始版本：** 18

**装饰器类型：** @ComponentV2

<!--Device-unnamed-export declare struct LoadingDialogV2--><!--Device-unnamed-export declare struct LoadingDialogV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AdvancedDialogV2OnCheckedChange, LoadingDialogV2, AdvancedDialogV2Button, AdvancedDialogV2ButtonAction, AlertDialogV2, CustomContentDialogV2, PopoverDialogV2Options, PopoverDialogV2, SelectDialogV2, PopoverDialogV2OnVisibleChange, TipsDialogV2, AdvancedDialogV2ButtonOptions, ConfirmDialogV2 } from '@kit.ArkUI';
```

## content

```TypeScript
content?: ResourceStr
```

加载弹出框内容。

默认为空。

**说明：** 内容超过十行会显示“...”。

**类型：** ResourceStr

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-LoadingDialogV2-content?: ResourceStr--><!--Device-LoadingDialogV2-content?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

