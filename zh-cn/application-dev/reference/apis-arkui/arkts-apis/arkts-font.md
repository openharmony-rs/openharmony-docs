# @ohos.font

本模块提供注册自定义字体。

> **说明：**
>
> - 本模块功能依赖UI的执行上下文，不可在[UI上下文不明确](../../../../ui/arkts-global-interface.md#ui上下文不明确)的地方使用，参见
> [UIContext](arkts-arkui-uicontext.md)说明。
>
> - 推荐使用字体引擎的[loadFontSync](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-fontcollection-c.md#loadfontsync-1)接口注册自定义字体。

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getFontByName](arkts-arkui-getfontbyname-f.md#getfontbyname-1) | 根据传入的系统字体名称获取系统字体的相关信息。@link @ohos.arkui.UIContext}中的&gt; [getFont](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getfont)方法获取&gt; [Font](arkts-arkui-uicontext.md)对象，然后通过该对象进行调用。且直接使用getFontByName可能导致&gt; [UI上下文不明确](../../../../ui/arkts-global-interface.md#ui上下文不明确)的问题。&gt;&gt; - 从API version 10开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的&gt; [getFont](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getfont)方法获取当前UI上下文关联的&gt; [Font](arkts-arkui-uicontext.md)对象。 |
| [getSystemFontList](arkts-arkui-getsystemfontlist-f.md#getsystemfontlist-1) | 获取系统字体列表。该接口仅在PC/2in1设备上生效，在其他设备上返回空数组。推荐使用[getSystemFontFullNamesByType](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-getsystemfontfullnamesbytype-f.md#getsystemfontfullnamesbytype-1)接口获取系统最新支持的字体列表数据。@link @ohos.arkui.UIContext}中的&gt; [getFont](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getfont)方法获取&gt; [Font](arkts-arkui-uicontext.md)对象，然后通过该对象进行调用。且直接使用getSystemFontList可能导致&gt; [UI上下文不明确](../../../../ui/arkts-global-interface.md#ui上下文不明确)的问题。&gt;&gt; - 从API version 10开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的&gt; [getFont](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getfont)方法获取当前UI上下文关联的&gt; [Font](arkts-arkui-uicontext.md)对象。 |
| [getUIFontConfig](arkts-arkui-getuifontconfig-f.md#getuifontconfig-1) | 获取系统字体配置文件的UI字体配置信息。该接口仅支持获取配置文件内的信息以及当UI上下文不明确时可能返回undefined，如果想要获取全量的字体配置信息，推荐使用字体引擎的[getSystemFontFullNamesByType](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-getsystemfontfullnamesbytype-f.md#getsystemfontfullnamesbytype-1)接口。 |
| [registerFont](arkts-arkui-registerfont-f.md#registerfont-1) | 在字体管理中注册自定义字体。该接口为异步接口，不支持并发调用。@link @ohos.arkui.UIContext}中的&gt; [getFont](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getfont)方法获取&gt; [Font](arkts-arkui-uicontext.md)对象，然后通过该对象进行调用。且直接使用registerFont可能导致&gt; [UI上下文不明确](../../../../ui/arkts-global-interface.md#ui上下文不明确)的问题。&gt;&gt; - 从API version 10开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的&gt; [getFont](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getfont)方法获取当前UI上下文关联的&gt; [Font](arkts-arkui-uicontext.md)对象。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [FontInfo](arkts-arkui-fontinfo-i.md) | 字体的详细信息。 |
| [FontOptions](arkts-arkui-fontoptions-i.md) | 注册的自定义字体信息。@link @ohos.arkui.UIContext}中的&gt; [getFont](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getfont)方法获取当前UI上下文关联的&gt; [Font](arkts-arkui-uicontext.md)对象。 |
| [UIFontAdjustInfo](arkts-arkui-uifontadjustinfo-i.md) | 系统的UI字体配置信息。 |
| [UIFontAliasInfo](arkts-arkui-uifontaliasinfo-i.md) | 系统的UI字体配置信息。 |
| [UIFontConfig](arkts-arkui-uifontconfig-i.md) | 系统的UI字体配置信息。 |
| [UIFontFallbackGroupInfo](arkts-arkui-uifontfallbackgroupinfo-i.md) | 系统的UI字体配置信息。 |
| [UIFontFallbackInfo](arkts-arkui-uifontfallbackinfo-i.md) | 系统的UI字体配置信息。 |
| [UIFontGenericInfo](arkts-arkui-uifontgenericinfo-i.md) | 系统的UI字体配置信息。 |

