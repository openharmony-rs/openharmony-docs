# @ohos.font

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace font--><!--Device-unnamed-declare namespace font-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { font } from '@kit.ArkUI';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getUIFontConfig](arkts-arkui-font-getuifontconfig-f.md) | 获取系统字体配置文件的UI字体配置信息。 该接口仅支持获取配置文件内的信息以及当UI上下文不明确时可能返回undefined，如果想要获取全量的字体配置信息，推荐使用字体引擎的 [getSystemFontFullNamesByType](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-getsystemfontfullnamesbytype-f.md) 接口。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [FontInfo](arkts-arkui-font-fontinfo-i.md) |  |
| [FontOptions](arkts-arkui-font-fontoptions-i.md) |  |
| [UIFontAdjustInfo](arkts-arkui-font-uifontadjustinfo-i.md) |  |
| [UIFontAliasInfo](arkts-arkui-font-uifontaliasinfo-i.md) |  |
| [UIFontConfig](arkts-arkui-font-uifontconfig-i.md) |  |
| [UIFontFallbackGroupInfo](arkts-arkui-font-uifontfallbackgroupinfo-i.md) |  |
| [UIFontFallbackInfo](arkts-arkui-font-uifontfallbackinfo-i.md) |  |
| [UIFontGenericInfo](arkts-arkui-font-uifontgenericinfo-i.md) |  |

