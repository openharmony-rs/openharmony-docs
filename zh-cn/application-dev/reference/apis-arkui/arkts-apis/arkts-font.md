# @ohos.font

本模块提供注册自定义字体。

> **说明：**
>
> - 本模块功能依赖UI的执行上下文，不可在[UI上下文不明确](../../../../ui/arkts-global-interface.md#ui上下文不明确)的地方使用，参见
> [UIContext](arkts-arkui-uicontext.md)说明。
>
> - 推荐使用字体引擎的[loadFontSync](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontcollection-c.md#loadFontSync-1)接口注册自定义字体。

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getFontByName](arkts-arkui-font-getfontbyname-f.md#getFontByName-1) | 根据传入的系统字体名称获取系统字体的相关信息。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; -getFontByName需要先通过[UIContext](arkts-arkui-uicontext.md)中的<br/>&gt; [getFont](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getfont)方法获取<br/>&gt; [Font](arkts-arkui-uicontext.md)对象，然后通过该对象进行调用。且直接使用getFontByName可能导致<br/>&gt; [UI上下文不明确](../../../../ui/arkts-global-interface.md#ui上下文不明确)的问题。<br/>&gt;<br/>&gt; - 从API version 10开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的<br/>&gt; [getFont](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getfont)方法获取当前UI上下文关联的<br/>&gt; [Font](arkts-arkui-uicontext.md)对象。<br/> |
| [getSystemFontList](arkts-arkui-font-getsystemfontlist-f.md#getSystemFontList-1) | 获取系统字体列表。<br/><br/>该接口仅在PC/2in1设备上生效，在其他设备上返回空数组。<br/><br/>推荐使用[getSystemFontFullNamesByType](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-getsystemfontfullnamesbytype-f.md#getSystemFontFullNamesByType-1)接口获取系统最新支持的字体列表数据。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; -getSystemFontList需要先通过[UIContext](arkts-arkui-uicontext.md)中的<br/>&gt; [getFont](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getfont)方法获取<br/>&gt; [Font](arkts-arkui-uicontext.md)对象，然后通过该对象进行调用。且直接使用getSystemFontList可能导致<br/>&gt; [UI上下文不明确](../../../../ui/arkts-global-interface.md#ui上下文不明确)的问题。<br/>&gt;<br/>&gt; - 从API version 10开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的<br/>&gt; [getFont](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getfont)方法获取当前UI上下文关联的<br/>&gt; [Font](arkts-arkui-uicontext.md)对象。<br/> |
| [getUIFontConfig](arkts-arkui-font-getuifontconfig-f.md#getUIFontConfig-1) | 获取系统字体配置文件的UI字体配置信息。<br/><br/>该接口仅支持获取配置文件内的信息以及当UI上下文不明确时可能返回undefined，如果想要获取全量的字体配置信息，推荐使用字体引擎的<br/>[getSystemFontFullNamesByType](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-getsystemfontfullnamesbytype-f.md#getSystemFontFullNamesByType-1)接口。<br/> |
| [registerFont](arkts-arkui-font-registerfont-f.md#registerFont-1) | 在字体管理中注册自定义字体。<br/><br/>该接口为异步接口，不支持并发调用。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; -registerFont需要先通过[UIContext](arkts-arkui-uicontext.md)中的<br/>&gt; [getFont](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getfont)方法获取<br/>&gt; [Font](arkts-arkui-uicontext.md)对象，然后通过该对象进行调用。且直接使用registerFont可能导致<br/>&gt; [UI上下文不明确](../../../../ui/arkts-global-interface.md#ui上下文不明确)的问题。<br/>&gt;<br/>&gt; - 从API version 10开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的<br/>&gt; [getFont](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getfont)方法获取当前UI上下文关联的<br/>&gt; [Font](arkts-arkui-uicontext.md)对象。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [FontInfo](arkts-arkui-font-fontinfo-i.md) | 字体的详细信息。<br/> |
| [FontOptions](arkts-arkui-font-fontoptions-i.md) | 注册的自定义字体信息。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 直接使用font可能导致[UI上下文不明确](../../../../ui/arkts-global-interface.md#ui上下文不明确)的问题，推荐通过使用<br/>&gt; [UIContext](arkts-arkui-uicontext.md)中的<br/>&gt; [getFont](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getfont)方法获取当前UI上下文关联的<br/>&gt; [Font](arkts-arkui-uicontext.md)对象。<br/> |
| [UIFontAdjustInfo](arkts-arkui-font-uifontadjustinfo-i.md) | 系统的UI字体配置信息。<br/> |
| [UIFontAliasInfo](arkts-arkui-font-uifontaliasinfo-i.md) | 系统的UI字体配置信息。<br/> |
| [UIFontConfig](arkts-arkui-font-uifontconfig-i.md) | 系统的UI字体配置信息。<br/> |
| [UIFontFallbackGroupInfo](arkts-arkui-font-uifontfallbackgroupinfo-i.md) | 系统的UI字体配置信息。<br/> |
| [UIFontFallbackInfo](arkts-arkui-font-uifontfallbackinfo-i.md) | 系统的UI字体配置信息。<br/> |
| [UIFontGenericInfo](arkts-arkui-font-uifontgenericinfo-i.md) | 系统的UI字体配置信息。<br/> |

