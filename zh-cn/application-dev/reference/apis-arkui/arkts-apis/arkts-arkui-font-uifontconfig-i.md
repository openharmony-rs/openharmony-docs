# UIFontConfig

系统的UI字体配置信息。

**起始版本：** 11

<!--Device-font-interface UIFontConfig--><!--Device-font-interface UIFontConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { font } from '@kit.ArkUI';
```

## fallbackGroups

```TypeScript
fallbackGroups: Array<UIFontFallbackGroupInfo>
```

备用字体集。

**类型：** Array&lt;UIFontFallbackGroupInfo&gt;

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIFontConfig-fallbackGroups: Array<UIFontFallbackGroupInfo>--><!--Device-UIFontConfig-fallbackGroups: Array<UIFontFallbackGroupInfo>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontDir

```TypeScript
fontDir: Array<string>
```

系统字体文件所在的路径。

**类型：** Array&lt;string&gt;

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIFontConfig-fontDir: Array<string>--><!--Device-UIFontConfig-fontDir: Array<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## generic

```TypeScript
generic: Array<UIFontGenericInfo>
```

系统所支持的通用字体集列表。

**类型：** Array&lt;UIFontGenericInfo&gt;

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIFontConfig-generic: Array<UIFontGenericInfo>--><!--Device-UIFontConfig-generic: Array<UIFontGenericInfo>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

