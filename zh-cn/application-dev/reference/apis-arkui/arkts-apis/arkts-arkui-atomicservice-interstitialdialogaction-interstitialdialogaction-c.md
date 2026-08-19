# InterstitialDialogAction

InterstitialDialogAction弹框在原子化服务中用于在保持当前的上下文环境时，临时展示用户需关注的信息或待处理的操作，用户点击弹框的不同区域可以触发对应的回调动作。 > **说明：** > > 该组件从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**起始版本：** 12

<!--Device-unnamed-export declare class InterstitialDialogAction--><!--Device-unnamed-export declare class InterstitialDialogAction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { InterstitialDialogAction, IconStyle, TitlePosition, BottomOffset } from '@kit.ArkUI';
```

## closeDialog

```TypeScript
closeDialog(): void
```

关闭弹框。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-InterstitialDialogAction-closeDialog(): void--><!--Device-InterstitialDialogAction-closeDialog(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(dialogOptions: DialogOptions)
```

InterstitialDialogAction的构造函数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-InterstitialDialogAction-constructor(dialogOptions: DialogOptions)--><!--Device-InterstitialDialogAction-constructor(dialogOptions: DialogOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dialogOptions | [DialogOptions](arkts-arkui-atomicservice-interstitialdialogaction-dialogoptions-i.md) | 是 | Creates a new dialog action object. |

## openDialog

```TypeScript
openDialog(): void
```

打开弹框。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-InterstitialDialogAction-openDialog(): void--><!--Device-InterstitialDialogAction-openDialog(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

