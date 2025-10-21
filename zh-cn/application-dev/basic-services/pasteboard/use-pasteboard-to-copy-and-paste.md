# 使用剪贴板进行复制粘贴
<!--Kit: Basic Services Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @yangxiaodong41-->
<!--Designer: @guo867-->
<!--Tester: @maxiaorong-->
<!--Adviser: @fang-jinxu-->

## 场景介绍

[剪贴板](../../reference/apis-basic-services-kit/js-apis-pasteboard.md)为开发者提供数据的复制粘贴能力。当需要使用复制粘贴等功能时，例如：复制文字内容到备忘录中粘贴，复制图库照片到文件管理粘贴，就可以通过剪贴板来完成。

## 约束限制

- 剪贴板内容包含剪贴板系统服务元数据和应用设置的数据，总大小上限默认为128MB，PC/2in1设备可通过系统配置修改上限，有效范围为128MB~2GB。
- 为保证剪贴板数据的准确性，同一时间只能支持一个复制操作。
- API version 12及之后，系统为提升用户隐私安全保护能力，剪贴板读取接口增加[权限管控](get-pastedata-permission-guidelines.md)。

## 使用基础数据类型进行复制粘贴

剪贴板支持使用基础数据类型进行复制粘贴，当前支持的基础数据类型有文本、HTML、URI、Want、PixelMap。ArkTS接口与NDK接口支持数据类型不完全一致，使用时须匹配接口支持类型。

新开发的应用建议使用本方案实现复制粘贴功能。

### ArkTS接口与NDK接口数据类型对应关系
| ArkTS数据类型 | NDK数据类型                                                                                                                                        |
| -------- |----------------------------------------------------------------------------------------------------------------------------------------|
| MIMETYPE_PIXELMAP : "pixelMap" | UDMF_META_OPENHARMONY_PIXEL_MAP : "openharmony.pixel-map" |
| MIMETYPE_TEXT_HTML : "text/html" | UDMF_META_HTML : "general.html" |
| MIMETYPE_TEXT_PLAIN : "text/plain" | UDMF_META_PLAIN_TEXT : "general.plain-text" |
| MIMETYPE_TEXT_URI : "text/uri" | UDMF_META_GENERAL_FILE_URI : "general.file-uri" |
| MIMETYPE_TEXT_WANT : "text/want" | NDK接口不支持该数据类型。 |

ArkTS数据类型对应剪贴板类型，详见[ohos.pasteboard](../../reference/apis-basic-services-kit/js-apis-pasteboard.md)。NDK数据类型对应统一数据管理框架，详见[UDMF](../../reference/apis-arkdata/capi-udmf.md)。

### 接口说明

详细接口见[接口文档](../../reference/apis-basic-services-kit/js-apis-pasteboard.md#getdata9)。

使用剪贴板getData接口获取到uri类型数据之后，请使用文件管理的[fs.copy](../../reference/apis-core-file-kit/js-apis-file-fs.md#fscopy11)接口获取文件。

| 名称 | 说明                                                                                                                                        |
| -------- |----------------------------------------------------------------------------------------------------------------------------------------|
| setData(data: PasteData, callback: AsyncCallback&lt;void&gt;): void | 将数据写入系统剪贴板，使用callback异步回调。 |
| setData(data: PasteData): Promise&lt;void&gt; | 将数据写入系统剪贴板，使用Promise异步回调。 |
| getData( callback: AsyncCallback&lt;PasteData&gt;): void | 读取系统剪贴板内容，使用callback异步回调。 |
| getData(): Promise&lt;PasteData&gt; | 读取系统剪贴板内容，使用Promise异步回调。 |
| getDataSync(): PasteData | 读取系统剪贴板内容, 此接口为同步接口，不能与SetData同线程调用。 |

### 示例代码

<!-- @[pasteboard_usedata](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/pasteboard/pasteboard_arkts_sample/entry/src/main/ets/pages/PasteboardModel.ets) -->

## 使用统一数据类型进行复制粘贴

为了方便剪贴板与其他应用间进行数据交互，减少数据类型适配的工作量，剪贴板支持使用统一数据对象进行复制粘贴。详细的统一数据对象请见[标准化数据通路](../../reference/apis-arkdata/js-apis-data-unifiedDataChannel.md)文档介绍。

剪贴板支持使用基础数据类型进行复制粘贴，当前支持的基础数据类型有文本、HTML。ArkTS接口与NDK接口支持数据类型不完全一致，使用时须匹配接口支持类型。

### 接口说明

详细接口见[接口文档](../../reference/apis-basic-services-kit/js-apis-pasteboard.md#getunifieddata12)。

| 名称 | 说明                                                                                                                                        |
| -------- |----------------------------------------------------------------------------------------------------------------------------------------|
| setUnifiedData(data: udc.UnifiedData): Promise\<void\> | 将统一数据对象的数据写入系统剪贴板。
| setUnifiedDataSync(data: udc.UnifiedData): void | 将统一数据对象的数据写入系统剪贴板，此接口为同步接口。                                                                                                                          |
| getUnifiedData(): Promise\<udc.UnifiedData\> | 从系统剪贴板中读取统一数据对象的数据。                                                                                                                          |
| getUnifiedDataSync(): udc.UnifiedData | 从系统剪贴板中读取统一数据对象的数据，此接口为同步接口。

### 示例代码

<!-- @[pasteboard_useudc](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/pasteboard/pasteboard_arkts_sample/entry/src/main/ets/pages/PasteboardModel.ets) -->

<!--RP1-->
<!--RP1End-->