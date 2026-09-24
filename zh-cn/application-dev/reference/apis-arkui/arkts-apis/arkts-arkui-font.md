# @ohos.font(注册自定义字体)

本模块提供注册自定义字体、获取系统字体列表、获取字体详细信息以及获取系统字体配置等能力，适用于应用需要使用自定义字体样式（如品牌字体、图标字体）或获取系统字体信息的场景。通过使用本模块，开发者可以实现品牌字体统一、提升用户界面美观度和一致性，满足多样化的设计需求。

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
| [getUIFontConfig](arkts-arkui-font-getuifontconfig-f.md) | 获取系统字体配置文件的UI字体配置信息。常用于需要分析或查看系统字体配置的场景，例如：字体管理工具、字体调试与诊断、字体配置信息展示等。 |
| [registerFont](arkts-arkui-font-registerfont-f.md) | 在字体管理中注册自定义字体。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [FontInfo](arkts-arkui-font-fontinfo-i.md) | 字体的详细信息。 |
| [FontOptions](arkts-arkui-font-fontoptions-i.md) | 注册的自定义字体信息。 |
| [UIFontAdjustInfo](arkts-arkui-font-uifontadjustinfo-i.md) | 字体原本的weight值和显示实际值的映射列表。 |
| [UIFontAliasInfo](arkts-arkui-font-uifontaliasinfo-i.md) | 别名列表。 |
| [UIFontConfig](arkts-arkui-font-uifontconfig-i.md) | 系统的UI字体配置信息。 |
| [UIFontFallbackGroupInfo](arkts-arkui-font-uifontfallbackgroupinfo-i.md) | 备用字体集。 |
| [UIFontFallbackInfo](arkts-arkui-font-uifontfallbackinfo-i.md) | 该字体集的备用字体。 |
| [UIFontGenericInfo](arkts-arkui-font-uifontgenericinfo-i.md) | 系统所支持的通用字体集列表。 |
