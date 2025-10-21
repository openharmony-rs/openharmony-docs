# 使用剪贴板进行复制粘贴 (C/C++)
<!--Kit: Basic Services Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @yangxiaodong41-->
<!--Designer: @guo867-->
<!--Tester: @maxiaorong-->
<!--Adviser: @fang-jinxu-->

## 场景介绍

剪贴板为开发者提供数据的复制粘贴能力。支持对纯文本、超文本、URI等内容的操作。

## 基本概念

- [**OH_PasteboardObserver**](../../reference/apis-basic-services-kit/capi-pasteboard-oh-pasteboardobserver.md)：剪贴板数据变更观察者对象，用以监听剪贴板数据变更事件。
- [**OH_Pasteboard**](../../reference/apis-basic-services-kit/capi-pasteboard-oh-pasteboard.md)：剪贴板对象，用来进行查询、写入等操作。
- [**OH_UdmfData**](../../reference/apis-arkdata/capi-udmf-oh-udmfdata.md)：统一数据对象。

## 约束限制

- 剪贴板内容包含剪贴板系统服务元数据和应用设置的数据，总大小上限默认为128MB，PC/2in1设备可通过系统配置修改上限，有效范围为128MB~2GB。
- 为保证剪贴板数据的准确性，同一时间只能支持一个复制操作。
- 当前支持的数据类型：纯文本类型(OH_UdsPlainText)、超文本标记语言类型(OH_UdsHtml)、文件Uri类型(OH_UdsFileUri)、像素图片类型(OH_UdsPixelMap)、超链接类型(OH_UdsHyperlink)、桌面图标类型(OH_UdsAppItem)、自定义类型。ArkTS接口与NDK接口支持数据类型不完全一致，使用时须匹配接口支持类型，详情见[ArkTS接口与NDK接口数据类型对应关系](../pasteboard/use-pasteboard-to-copy-and-paste.md)。
- 自定义类型数据在复制粘贴时，指定的类型名称不能和已有的类型名称重复。
- API version 12及之后，系统为提升用户隐私安全保护能力，剪贴板读取接口增加[权限管控](get-pastedata-permission-guidelines.md)。
- API version 12中新增的复制、粘贴接口[setUnifiedData](../../reference/apis-basic-services-kit/js-apis-pasteboard.md#setunifieddata12)/[getUnifiedData](../../reference/apis-basic-services-kit/js-apis-pasteboard.md#getunifieddata12)，和本文档中的复制、粘贴接口[OH_Pasteboard_SetData](../../reference/apis-basic-services-kit/capi-oh-pasteboard-h.md#oh_pasteboard_setdata)/[OH_Pasteboard_GetData](../../reference/apis-basic-services-kit/capi-oh-pasteboard-h.md#oh_pasteboard_getdata)，当前相互独立，进行写入、读取操作时请使用对应配套接口。

## 接口说明

详细接口见[Pasteboard文档](../../reference/apis-basic-services-kit/capi-pasteboard.md)。

| 接口名称                                                     | 描述                                                    |
| ------------------------------------------------------------ | ------------------------------------------------------- |
| OH_PasteboardObserver* OH_PasteboardObserver_Create()        | 创建一个剪贴板数据变更观察者对象。                      |
| OH_PasteboardObserver_Destroy(OH_PasteboardObserver* observer) | 销毁剪贴板数据变更观察者对象。                          |
| int OH_PasteboardObserver_SetData(OH_PasteboardObserver* observer, void* context, const Pasteboard_Notify callback, const Pasteboard_Finalize finalize) | 将剪贴板变更回调函数设置到剪贴板数据变更观察者对象中。  |
| OH_Pasteboard* OH_Pasteboard_Create()                        | 创建一个剪贴板实例。                                    |
| void OH_Pasteboard_Destroy(OH_Pasteboard* pasteboard)        | 销毁剪贴板实例。                                        |
| int OH_Pasteboard_Subscribe(OH_Pasteboard* pasteboard, int type, const OH_PasteboardObserver* observer) | 订阅剪贴板的数据变更。                                  |
| int OH_Pasteboard_Unsubscribe(OH_Pasteboard* pasteboard, int type, const OH_PasteboardObserver* observer) | 取消对剪贴板数据变更的订阅。                            |
| bool OH_Pasteboard_IsRemoteData(OH_Pasteboard* pasteboard)   | 判断剪贴板中的数据是否来自远端设备。                    |
| int OH_Pasteboard_GetDataSource(OH_Pasteboard* pasteboard, char* source, unsigned int len) | 获取剪贴板中数据的数据源。                              |
| bool OH_Pasteboard_HasType(OH_Pasteboard* pasteboard, const char* type) | 判断剪贴板中是否有指定类型的数据。                      |
| bool OH_Pasteboard_HasData(OH_Pasteboard* pasteboard)        | 检查剪贴板中是否有数据。                                |
| OH_UdmfData* OH_Pasteboard_GetData(OH_Pasteboard* pasteboard, int* status) | 获取剪贴板中的数据。                                    |
| int OH_Pasteboard_SetData(OH_Pasteboard* pasteboard, OH_UdmfData* data) | 向剪贴板中写入数据。                                    |
| int OH_Pasteboard_ClearData(OH_Pasteboard* pasteboard)       | 清空剪贴板中的数据。                                    |
| void (\*Pasteboard_Notify)(void\* context, Pasteboard_NotifyType type) | 剪贴板中数据变更回调函数。                              |
| void (\*Pasteboard_Finalize)(void\* context)                 | 剪贴板数据变更观察者对象销毁时，释放context上下文资源。 |

## 开发步骤

1. 添加动态链接库。

   ```CMake
   # CMakeLists.txt中添加以下lib
   libudmf.so
   libpasteboard.so
   ```

2. 引用头文件。

    <!-- @[pasteboard_native2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/pasteboard/pasteboard_NDK_sample/entry/src/main/cpp/napi_init.cpp) -->

3. 定义剪贴板变化监听的回调函数。

    <!-- @[pasteboard_native3](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/pasteboard/pasteboard_NDK_sample/entry/src/main/cpp/napi_init.cpp) -->

4. 订阅剪贴板变化。

    <!-- @[pasteboard_native4](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/pasteboard/pasteboard_NDK_sample/entry/src/main/cpp/napi_init.cpp) -->

5. 向剪贴板写入数据。

    <!-- @[pasteboard_native5](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/pasteboard/pasteboard_NDK_sample/entry/src/main/cpp/napi_init.cpp) -->

6. 从剪贴板读取数据。

    <!-- @[pasteboard_native6](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/pasteboard/pasteboard_NDK_sample/entry/src/main/cpp/napi_init.cpp) -->
