# getUIFontConfig

## 导入模块

```TypeScript
import { font } from '@kit.ArkUI';
```

## getUIFontConfig

```TypeScript
function getUIFontConfig(): UIFontConfig
```

获取系统字体配置文件的UI字体配置信息。

该接口仅支持获取配置文件内的信息以及当UI上下文不明确时可能返回undefined，如果想要获取全量的字体配置信息，推荐使用字体引擎的[getSystemFontFullNamesByType](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-getsystemfontfullnamesbytype-f.md#getsystemfontfullnamesbytype-1)接口。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-font-function getUIFontConfig(): UIFontConfig--><!--Device-font-function getUIFontConfig(): UIFontConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UIFontConfig](arkts-arkui-font-uifontconfig-i.md) | Returns the ui font config |

