# @ohos.uiAppearance

用户界面外观提供获取系统外观的一些基础能力，包括获取深浅色模式、字体大小缩放比例、字体粗细缩放比例。 > **说明：** > 从API version 20开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-unnamed-declare namespace uiAppearance--><!--Device-unnamed-declare namespace uiAppearance-End-->

**系统能力：** SystemCapability.ArkUI.UiAppearance

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getDarkMode](arkts-arkui-uiappearance-getdarkmode-f-sys.md#getDarkMode) | 获取系统当前的深浅色模式配置。适用于需要根据系统外观模式动态适配应用UI主题的场景，例如应用内实现深色/浅色主题风格自动切换。 &lt;!--Del--&gt; |
| [getFontScale](arkts-arkui-uiappearance-getfontscale-f-sys.md#getFontScale) | 获取系统当前的字体大小缩放比例。该比例为系统设置中用户配置的字体大小相对于默认字体大小的倍数，取值范围请参考系统字体大小设置。开发者可基于该比例值调整应用内字体大小，以适配用户的字体偏好设置。 &lt;!--Del--&gt; |
| [getFontWeightScale](arkts-arkui-uiappearance-getfontweightscale-f-sys.md#getFontWeightScale) | 获取系统当前的字体粗细缩放比例。该比例为系统设置中用户配置的字体粗细相对于默认字体粗细的倍数，取值范围请参考系统字体粗细设置。开发者可基于该比例值调整应用内字体粗细，以适配用户的字体粗细偏好设置。 &lt;!--Del--&gt; |
| [setDarkMode](arkts-arkui-uiappearance-setdarkmode-f-sys.md#setDarkMode) | 设置系统深浅色模式，修改系统级配色方案配置。设置后，所有跟随系统配色方案的应用将自动切换至对应模式。使用callback异步回调。 |
| [setDarkMode](arkts-arkui-uiappearance-setdarkmode-f-sys.md#setDarkMode（系统接口）) | 设置系统深浅色模式，修改系统级配色方案配置。设置后，所有跟随系统配色方案的应用将自动切换至对应模式。使用Promise异步回调。 |
| [setFontScale](arkts-arkui-uiappearance-setfontscale-f-sys.md#setFontScale) | 设置系统字体大小。 |
| [setFontWeightScale](arkts-arkui-uiappearance-setfontweightscale-f-sys.md#setFontWeightScale) | 设置系统字体粗细。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DarkMode](arkts-arkui-uiappearance-darkmode-e-sys.md) | 深浅色模式枚举，用于配置系统的深色或浅色模式。 \| 名称 \| 值 \| 说明 \| \| -- \| -- \| -- \| \| ALWAYS_DARK \| 0 \| 系统始终为深色。 \| \| ALWAYS_LIGHT \| 1 \| 系统始终为浅色。 \| |
<!--DelEnd-->

