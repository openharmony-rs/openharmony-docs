# ShowToastOptions

定义ShowToast的选项。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** ShowToastOptions

<!--Device-unnamed-export interface ShowToastOptions--><!--Device-unnamed-export interface ShowToastOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ShowActionMenuOptions, Button, ShowToastOptions, ShowDialogOptions, ShowDialogSuccessResponse } from '@kit.ArkUI';
```

## bottom

```TypeScript
bottom?: string | number
```

设置弹窗边框距离屏幕底部的位置。

**类型：** string \| number

**起始版本：** 5

**废弃版本：** 8

**替代接口：** bottom

<!--Device-ShowToastOptions-bottom?: string | number--><!--Device-ShowToastOptions-bottom?: string | number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: number
```

默认值1500ms，建议区间：1500ms-10000ms。若小于1500ms则取默认值，最大取值为10000ms。

**类型：** number

**起始版本：** 3

**废弃版本：** 8

**替代接口：** duration

<!--Device-ShowToastOptions-duration?: number--><!--Device-ShowToastOptions-duration?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## message

```TypeScript
message: string
```

显示的文本信息。

**类型：** string

**起始版本：** 3

**废弃版本：** 8

**替代接口：** message

<!--Device-ShowToastOptions-message: string--><!--Device-ShowToastOptions-message: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

