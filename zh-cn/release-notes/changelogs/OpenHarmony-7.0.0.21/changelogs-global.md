# 全球化子系统 Changelog

## cl.notofonts.1 notofonts三方件小语种字体升级变更

**访问级别**

公共能力

**变更原因**

当前版本存在错别字的问题，变更后可修复错别字和优化数学字符的显示。

**变更影响**

此变更涉及应用适配。

变更前：蒙古语（NotoSansMongolian-Regular.ttf）、天城体（NotoSansDevanagari[wdth,wght].ttf）、缅甸语（NotoSansMyanmar[wdth,wght].ttf）部分显示不正确。

变更后：蒙古语（NotoSansMongolian-Regular.ttf）、天城体（NotoSansDevanagari[wdth,wght].ttf）、缅甸语（NotoSansMyanmar[wdth,wght].ttf）显示正确，部分数学符号字体（NotoSansMath-Regular.ttf）显示变大。

**起始 API Level**

11

**变更发生版本**

从 OpenHarmony SDK 7.0.0.21 开始。

**变更的接口/组件**

不涉及

**适配指导**

数学符号变大后，显示更清晰，效果会更好。由于数学符号变大，可能出现界面排版变动，需要应用根据实际情况调整界面排版。