# ShowToastOptions

文本提示框的选项。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [ShowToastOptions](arkts-arkui-promptaction-showtoastoptions-i.md)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { prompt } from '@kit.ArkUI';
```

## bottom

```TypeScript
bottom?: string | number
```

设置弹窗边框距离屏幕底部的位置，无上限值，默认单位vp。

**类型：** string \| number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [bottom](arkts-arkui-promptaction-showtoastoptions-i.md#bottom)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: number
```

默认值1500ms，取值区间：1500ms-10000ms。若小于1500ms则取默认值，若大于10000ms则取上限值10000ms。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [duration](arkts-arkui-promptaction-showtoastoptions-i.md#duration)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## message

```TypeScript
message: string
```

显示的文本信息。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [message](arkts-arkui-promptaction-showtoastoptions-i.md#message)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
