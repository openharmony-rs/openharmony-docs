# ShowToastOptions

文本提示框的选项。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [ShowToastOptions](../../apis-na/arkts-apis/arkts-na-promptaction-showtoastoptions-i.md)

<!--Device-prompt-interface ShowToastOptions--><!--Device-prompt-interface ShowToastOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { prompt } from '@kit.ArkUI';
import { promptAction, LevelMode, ImmersiveMode, LevelOrder } from '@kit.ArkUI';
```

## bottom

```TypeScript
bottom?: string | number
```

设置弹窗边框距离屏幕底部的位置，无上限值，默认单位vp。

**类型：** string \| number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [bottom](../../apis-na/arkts-apis/arkts-na-promptaction-showtoastoptions-i.md#bottom)

<!--Device-ShowToastOptions-bottom?: string | number--><!--Device-ShowToastOptions-bottom?: string | number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: number
```

默认值1500ms，取值区间：1500ms-10000ms。若小于1500ms则取默认值，若大于10000ms则取上限值10000ms。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [duration](../../apis-na/arkts-apis/arkts-na-promptaction-showtoastoptions-i.md#duration)

<!--Device-ShowToastOptions-duration?: number--><!--Device-ShowToastOptions-duration?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## message

```TypeScript
message: string
```

显示的文本信息。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [message](../../apis-na/arkts-apis/arkts-na-promptaction-showtoastoptions-i.md#message)

<!--Device-ShowToastOptions-message: string--><!--Device-ShowToastOptions-message: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

