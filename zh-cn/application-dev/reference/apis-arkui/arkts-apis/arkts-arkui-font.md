# @ohos.font(注册自定义字体)

本模块提供注册自定义字体。

> **说明：** 
> 
> - 本模块功能依赖UI的执行上下文，不可在[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的地方使用，参见[UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)说明。
> 
> - 推荐使用字体引擎的[loadFontSync](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontcollection-c.md#loadfontsync)接口注册自定义字体。

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { font } from '@kit.ArkUI';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getFontByName](arkts-arkui-font-getfontbyname-f.md) | 根据传入的系统字体名称获取系统字体的相关信息。 |
| [getSystemFontList](arkts-arkui-font-getsystemfontlist-f.md) | 获取系统字体列表。 |
| [getUIFontConfig](arkts-arkui-font-getuifontconfig-f.md) | 获取系统字体配置文件的UI字体配置信息。 |
| [registerFont](arkts-arkui-font-registerfont-f.md) | 在字体管理中注册自定义字体。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [FontInfo](arkts-arkui-font-fontinfo-i.md) | 字体的详细信息。 |
| [FontOptions](arkts-arkui-font-fontoptions-i.md) | 注册的自定义字体信息。 |
| [UIFontAdjustInfo](arkts-arkui-font-uifontadjustinfo-i.md) | 系统的UI字体配置信息。 |
| [UIFontAliasInfo](arkts-arkui-font-uifontaliasinfo-i.md) | 系统的UI字体配置信息。 |
| [UIFontConfig](arkts-arkui-font-uifontconfig-i.md) | 系统的UI字体配置信息。 |
| [UIFontFallbackGroupInfo](arkts-arkui-font-uifontfallbackgroupinfo-i.md) | 系统的UI字体配置信息。 |
| [UIFontFallbackInfo](arkts-arkui-font-uifontfallbackinfo-i.md) | 系统的UI字体配置信息。 |
| [UIFontGenericInfo](arkts-arkui-font-uifontgenericinfo-i.md) | 系统的UI字体配置信息。 |
