# UIFontFallbackGroupInfo

系统的UI字体配置信息。

**起始版本：** 11

<!--Device-font-interface UIFontFallbackGroupInfo--><!--Device-font-interface UIFontFallbackGroupInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { font } from '@kit.ArkUI';
```

## fallback

```TypeScript
fallback: Array<UIFontFallbackInfo>
```

表示以下列表为该字体集的备用字体，如果fontSetName为""，表示可以作为所有字体集的备用字体。

**类型：** Array<UIFontFallbackInfo>

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIFontFallbackGroupInfo-fallback: Array<UIFontFallbackInfo>--><!--Device-UIFontFallbackGroupInfo-fallback: Array<UIFontFallbackInfo>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSetName

```TypeScript
fontSetName: string
```

备用字体集所对应的字体集名称。

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIFontFallbackGroupInfo-fontSetName: string--><!--Device-UIFontFallbackGroupInfo-fontSetName: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

