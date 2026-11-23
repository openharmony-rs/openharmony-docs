# 采集图文信息
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lushi871202-->
<!--Designer: @lushi871202-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

从API版本26.1.0开始，应用可以通过ArkUI NDK接口采集指定节点的图片，得到该节点对应的PixelMap。采集以节点ID为单位进行：一次请求提交1到20个互不重复的节点ID，框架在目标UI实例的UI线程回调一次，每个节点ID在结果集合中对应一个结果项，应用按节点ID逐项取出PixelMap。

图片来源按节点类型区分。目标为[Image](../reference/apis-arkui/arkui-ts/ts-basic-components-image.md)节点且能取到源图时，接口返回该组件的完整源图，像素尺寸与页面上的显示尺寸无关；取不到源图时按节点边界截取该节点范围内的渲染内容。其他节点统一按节点边界截取该节点范围内的渲染内容。节点是否可见不影响能否采集。

采集通常与其他UI信息能力配合使用。应用可以先读取控件树，从结果中获取目标节点的整数节点ID，再按节点ID采集图片，从而避免自行维护节点标识与节点ID的对应关系。

本专题按以下顺序说明：先介绍接口与调用方式，并说明结果分层、节点ID数量、图片来源、页面文本JSON结构与消费释放规则（[接口说明](#接口说明)），然后结合示例工程给出完整开发流程（[开发流程](#开发流程)），最后列出典型问题与处理方式（[常见问题](#常见问题)）。

本篇介绍节点图片采集和页面文本采集能力。从API版本26.1.0开始，应用还可以通过[OH_ArkUI_NativeModule_UIAgentGetPageText](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagentgetpagetext)在UI线程同步采集当前ArkUI页面的文本信息，并以JSON格式输出。

> **说明：**
>
> - 本篇示例仅提供核心接口的调用方法，完整的示例工程请参考<!--RP1-->[UI信息采集和交互注入示例工程](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection)<!--RP1End-->。

## 约束与限制

采集前应确认SDK与设备实现的匹配关系、上下文来源、请求规模以及结果对象的所有权，以下条件会影响请求是否被受理或结果是否可用。

- 使用包含`ui_info_collection.h`中相关声明的配套SDK，并确保运行设备提供与SDK匹配的实现。头文件与库符号齐备时，仍需确认设备实现已提供该能力。
- 上下文句柄必须指向目标UI实例，并在请求处理期间保持有效。句柄无法解析到目标实例时返回[ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)，例如句柄为空、页面或窗口已经销毁，或句柄来自其他UI实例。
- 页面或窗口销毁后不继续使用原上下文发起请求；请求受理后实例失效的，回调返回[ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)且不返回结果集合。
- 单次请求的节点ID数量为1到20个，且不得重复。
- 每个被受理的节点ID都有一个结果项，节点找不到或图片采集失败也占一项；回调的整体错误码只表示这一批的总体结果，失败项需要在取出结果时逐项判断。
- Image节点能取到源图时，采集结果按源图像素计量，与页面上的显示尺寸无关；取不到源图时按节点边界截取。其他节点统一按节点边界截取，像素尺寸随节点在页面上的显示尺寸变化。需要与显示尺寸一致的图片时，由应用自行缩放。
- 提交接口可以从任意线程调用；对被受理的请求，回调在目标UI实例的UI线程执行且仅执行一次。
- 同一UI实例上一次请求的回调未返回前，再次提交会被拒绝并返回[ARKUI_ERROR_CODE_COMMAND_UNFINISHED](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)。
- 取出的PixelMap所有权转移给应用，由应用调用[OH_PixelmapNative_Destroy](../reference/apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_destroy)释放。结果集合由应用调用[OH_ArkUI_NativeModule_ImageCollectionDestroy](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_imagecollectiondestroy)销毁，即使其中的结果项已全部取出。
- 避免逐帧采集或在失败后循环重试。按业务需要发起请求，处理完结果后再决定下一次操作。
- 页面文本采集接口[OH_ArkUI_NativeModule_UIAgentGetPageText](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagentgetpagetext)为同步接口，必须在目标UI实例的UI线程上调用。
- 调用页面文本采集接口前，应将接收结果的`OH_ArkUI_NativeModule_UIJsonWrapper*`指针初始化为`NULL`。调用成功时，对象所有权转移给应用，使用完毕后必须调用[OH_ArkUI_NativeModule_UIJsonWrapperDestroy](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy)释放内存。

## 接口说明

采集使用`<arkui/ui_info_collection.h>`中图像采集相关的三个函数和一个回调类型，编译时链接`libace_ndk.z.so`；通过N-API桥接调用时还需链接`libace_napi.z.so`。取出的PixelMap由Image Kit的接口处理。需包含`<multimedia/image_framework/image/pixelmap_native.h>`并链接`libpixelmap.so`；交给Image组件渲染时，用[OH_PixelmapNative_ConvertPixelmapNativeToNapi](../reference/apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_convertpixelmapnativetonapi)转换成ArkTS对象。完整声明、参数、起始版本以及各接口的返回值与错误码见[ui_info_collection.h](../reference/apis-arkui/capi-ui-info-collection-h.md)，常见失败情形见[常见问题](#常见问题)。

三个函数的用途、调用线程与对象所有权见下表。

| 接口 | 用途 | 调用线程与对象所有权 |
|---|---|---|
| [OH_ArkUI_NativeModule_GetImagesByNodeIdAsync](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_getimagesbynodeidasync) | 提交一次异步采集请求，指定上下文、节点ID数组、数量和回调。 | 可以从任意线程调用；nodeIds数组在函数返回前被复制，应用可在提交后释放自己的数组。 |
| [OH_ArkUI_NativeModule_ImageCollectionTakeItemByNodeId](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_imagecollectiontakeitembynodeid) | 从结果集合中取出指定节点ID对应的结果项。 | 在集合有效期内调用；成功时PixelMap所有权转移给应用，由应用释放。 |
| [OH_ArkUI_NativeModule_ImageCollectionDestroy](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_imagecollectiondestroy) | 销毁结果集合，释放尚未取出的PixelMap。 | 由集合的所有者调用一次；参数可以为空，此时不执行任何操作。 |

回调类型[OH_ArkUI_NativeModule_ImageCollectionCallback](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_imagecollectioncallback)用于接收本次请求的整体结果码与结果集合，每个被受理的请求回调一次。结果集合[OH_ArkUI_NativeModule_ImageCollection](../reference/apis-arkui/capi-arkui-nativemodule-oh-arkui-nativemodule-imagecollection.md)承载本次请求的全部结果项，只能通过取出接口访问其中的结果。

三个函数的调用顺序为：提交请求、在回调中按节点ID逐项取出结果并转换成ArkTS对象、最后销毁集合。提交返回成功只表示请求被受理，图片是否采集成功要在回调与结果项中判断。

### 结果的分层模型

一次采集会产生四个层次的返回值，分别对应提交、整体、单项和取出动作，判断某一层失败时不能套用另一层的结论。

| 层次 | 含义 | 处理方式 |
|---|---|---|
| 受理结果 | 提交接口的返回值，表示请求是否被受理。 | 非0表示请求被拒绝，不会再有回调，不需要等待结果。 |
| 整体结果 | 回调的errorCode，表示这一批的总体结果。 | 部分失败时仍会返回集合，需要逐项取出。 |
| 单项结果 | 取出接口的outItemError，表示单个节点ID的采集结果。 | 非0表示该项没有图片，只影响该项自身。 |
| 取出结果 | 取出接口的返回值，表示本次取出动作是否成功，与图片是否采集成功无关。 | 非0表示该节点ID不在集合中、已被取出或参数无效。 |

整体结果与单项结果还可能返回[ARKUI_ERROR_CODE_RESOURCE_EXHAUSTED](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)，分别表示集合分配失败与该节点生成图片所需的内存分配失败。

### 请求中的节点ID与数量

请求以整数节点ID定位目标，节点ID由[getUniqueId](../reference/apis-arkui/js-apis-arkui-frameNode.md#getuniqueid12)获取，与组件通过`id()`设置的字符串标识不是同一个值。结果集合按节点ID组织，每个被受理的节点ID都有一个结果项，应用可以按自己的请求顺序逐项取出并渲染，不依赖集合内部的排列。

- 数量为1到20个，且不得重复；越界或重复时请求被拒绝，返回值定义见[ArkUI_ErrorCode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)。
- 节点ID只在节点存在期间有效。节点被移除、页面重建或列表回收后，原有节点ID不再对应任何节点，采集该ID会得到[ARKUI_ERROR_CODE_NODE_NOT_FOUND](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)。
- 采集不要求节点处于可见状态，节点不在当前可见区域内也可以作为目标。

### 图片内容的取用规则

图片内容与像素尺寸取决于目标节点类型（含Image节点取不到源图的情形），返回值与所有权规则相同。

| 目标节点 | 返回的图片 | 说明 |
|---|---|---|
| Image节点 | 组件的完整源图。 | 像素尺寸为源图尺寸，不是页面上的显示尺寸。示例工程的源图为640×480，页面显示尺寸为96vp。 |
| Image节点（源图不可用） | 节点边界内的渲染内容。 | 与下一行的行为一致。 |
| 其他节点 | 节点边界内的渲染内容。 | 结果为该节点边界范围内的渲染内容，像素尺寸随节点在页面上的显示尺寸变化。 |

### 结果项的取出规则

每个结果项在集合有效期内只能取出一次，取出后集合不再持有该项的PixelMap。失败项同样需要取出，用于获取该节点的错误码。

- 采集成功：outPixelmap接收PixelMap，所有权转移到应用，由应用调用[OH_PixelmapNative_Destroy](../reference/apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_destroy)释放。
- 采集失败：outPixelmap被置为空指针，错误码写入outItemError，本次取出仍返回0。
- 同一节点ID重复取出、或传入不属于该集合的节点ID时，取出会失败，返回值定义见[ArkUI_ErrorCode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)。
- 取出接口不得与同一集合的其他集合操作接口并发调用。

### 集合的释放规则

回调返回的每个非空集合都必须销毁，包括所有结果项都已取出的情况。销毁集合只释放应用尚未取出的PixelMap，不会使已经转移给应用的PixelMap失效。

集合与其中的PixelMap分属两层所有权：PixelMap在取出时转移，集合在销毁时释放。应用如果把PixelMap转换成ArkTS对象使用，应在转换完成后及时释放native对象，不必与集合的销毁时机对齐。销毁集合同样不得与同一集合的其他集合操作接口并发调用。

### 页面文本采集接口

页面文本采集使用`<arkui/ui_info_collection.h>`中的[OH_ArkUI_NativeModule_UIAgentGetPageText](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagentgetpagetext)，并配合`<arkui/ui_json_wrapper.h>`中的JSON封装接口读取与释放结果，编译时链接`libace_ndk.z.so`。

| 接口 | 用途 | 调用线程与对象所有权 |
|---|---|---|
| [OH_ArkUI_NativeModule_UIAgentGetPageText](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagentgetpagetext) | 同步采集当前ArkUI页面的文本，并以JSON格式输出。 | 必须在目标UI实例的UI线程调用；成功时返回对象的所有权转移给应用。 |
| [OH_ArkUI_NativeModule_UIJsonWrapperGetData](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappergetdata) | 获取JSON封装对象中保存的只读UTF-8字符串指针。 | 借用对象，字符串内存在对象销毁前有效，调用方不得修改或释放。 |
| [OH_ArkUI_NativeModule_UIJsonWrapperGetSize](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappergetsize) | 获取JSON字符串的字节长度（不含末尾空字符）。 | 可在任意线程调用，不分配或释放资源。 |
| [OH_ArkUI_NativeModule_UIJsonWrapperDestroy](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy) | 销毁JSON封装对象并释放其占用的内存。 | 由对象所有者调用一次；销毁后不得再使用对象及其字符串指针。 |

调用成功时，返回的JSON对象顶层包含`schemaVersion`字段和`texts`数组（即使页面存在但没有符合条件的文本，也会返回`{"schemaVersion":1,"texts":[]}`）。`texts`数组中每个元素对应一个符合采集条件的文本组件，包含用于标识控件的整数`"id"`、相对于目标窗口的矩形区域`"rect"`（格式为`[x, y, width, height]`，单位为物理像素），以及表示文本内容的字符串`"content"`。

## 开发流程

以下步骤以示例工程为上下文，依次完成页面准备、节点ID获取、请求提交和结果展示。

### 准备工程与页面

通用NDK工程创建、ArkTS与Native桥接及构建配置见[基于NDK构建UI概述](ndk-build-ui-overview.md)和[接入ArkTS页面](ndk-access-the-arkts-page.md)。采集结果转换为ArkTS图片对象时，还需要Image Kit的PixelMap接口。

示例工程的Native构建脚本在链接`libace_ndk.z.so`与`libace_napi.z.so`之外，额外链接`libpixelmap.so`。

> **说明：**
>
> 采集接口以PixelMap形式返回结果，应用在Native侧获取该PixelMap后，按示例的方式转换成ArkTS对象再交给Image组件，或按业务需要处理像素数据。

采集接口要求上下文句柄指向目标页面的UI实例。示例工程通过页面上的[NodeContent](../reference/apis-arkui/js-apis-arkui-NodeContent.md)获取上下文。Native侧在其中挂载一个空节点，再用[OH_ArkUI_GetContextByNode](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_getcontextbynode)从该节点反查。实现见示例工程中的AttachImageAnchor与GetImageContext。也可以把页面上的[UIContext](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md)通过[OH_ArkUI_GetContextFromNapiValue](../reference/apis-arkui/capi-native-node-napi-h.md#oh_arkui_getcontextfromnapivalue)转换为[ArkUI_ContextHandle](../reference/apis-arkui/capi-arkui-nativemodule-arkui-context8h.md)，与从节点反查得到的是同一个UI实例的句柄。

### 获取目标节点ID

目标节点ID从页面的[UIContext](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md)获取：先通过[getFrameNodeById](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getframenodebyid12)按组件`id()`设置的字符串标识得到FrameNode，再调用[getUniqueId](../reference/apis-arkui/js-apis-arkui-frameNode.md#getuniqueid12)获取整数节点ID。

节点ID只在节点存在期间有效，示例在每次采集前重新读取，不缓存。[getFrameNodeById](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getframenodebyid12)返回空表示该标识当前没有对应节点，此时应放弃本次采集，不要用无效值提交请求；示例的单节点与批量入口未做该判断，实际应用需要自行补充。

### 提交采集请求

提交时把节点ID数组和回调交给采集接口，由框架在目标UI实例的UI线程回调一次。示例把回调结果包装为Promise，页面侧按异步流程处理。

以下代码块中的Arguments、ReadNodeIds、NumberProperty、ImageItem、ImageRequest、GetImageContext，以及页面代码中的failure、DOMAIN、TAG，均为示例工程自行实现的辅助函数、结构体或常量。本专题新介绍的接口仅为[接口说明](#接口说明)中的三个函数与回调类型，其余接口见各自参考文档。

提交时需要注意以下三点。

- 请求被拒绝时不会再有回调，示例直接把拒绝码作为受理结果返回，页面不会等待一个不会发生的回调。
- nodeIds数组在函数返回前已被复制，示例在提交后不再持有调用方数组。
- 同一UI实例上一次请求未完成时提交会返回[ARKUI_ERROR_CODE_COMMAND_UNFINISHED](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)，页面应在收到结果前禁用触发采集的交互，不要用连续提交的方式重试。

<!-- @[ndk_image_collect](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection/entry/src/main/cpp/napi_init.cpp) -->

``` C++
// 页面调用的桥接入口：collectImages(nodeIds)。
// 返回的Promise在请求受理后完成，结果包含受理结果与全部结果项。
napi_value CollectImages(napi_env env, napi_callback_info info)
{
    napi_value args[IMAGE_ARG_COUNT];
    if (!Arguments(env, info, IMAGE_ARG_COUNT, args)) {
        return nullptr;
    }
    auto context = GetImageContext(env);
    if (!context) {
        return nullptr;
    }
    std::vector<int32_t> nodeIds;
    if (!ReadNodeIds(env, args[IMAGE_NODE_IDS_ARG], nodeIds)) {
        return nullptr;
    }
    napi_value promise = nullptr;
    auto* request = new (std::nothrow) ImageRequest();
    if (request == nullptr || napi_create_promise(env, &request->deferred, &promise) != napi_ok) {
        delete request;
        napi_throw_error(env, nullptr, "Cannot create the image collection promise");
        return nullptr;
    }
    request->env = env;
    request->nodeIds = nodeIds;
    // 框架会在本函数返回前复制节点ID，request持有自己的副本，
    // 调用方可以立即释放数组。
    const auto code = OH_ArkUI_NativeModule_GetImagesByNodeIdAsync(context, request->nodeIds.data(),
        static_cast<uint32_t>(request->nodeIds.size()), OnImages, request);
    if (code != ARKUI_ERROR_CODE_NO_ERROR) {
        // 请求被拒绝：不会再收到回调，直接返回受理结果并结束。
        napi_value rejected = nullptr;
        napi_value empty = nullptr;
        if (napi_create_object(env, &rejected) == napi_ok && napi_create_array(env, &empty) == napi_ok) {
            NumberProperty(env, rejected, "submitError", static_cast<int32_t>(code));
            NumberProperty(env, rejected, "overallError", static_cast<int32_t>(code));
            napi_set_named_property(env, rejected, "items", empty);
            napi_resolve_deferred(env, request->deferred, rejected);
        }
        delete request;
    }
    return promise;
}
```

### 在回调中取出结果项

回调在目标UI实例的UI线程执行，结果集合在回调中转移给应用，由应用负责取出与销毁。示例在回调内按请求顺序取出全部结果项，并在回调返回前完成清理。

<!-- @[ndk_image_take_item](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection/entry/src/main/cpp/napi_init.cpp) -->

``` C++
// 每个被受理的请求在UI线程执行一次：取出并转换全部结果项，
// 返回前释放集合。
void OnImages(ArkUI_ErrorCode overallError, OH_ArkUI_NativeModule_ImageCollection* collection, void* userData)
{
    auto* request = static_cast<ImageRequest*>(userData);
    if (request == nullptr) {
        // 已无业务对象接收该结果：仍需销毁集合以释放其中的图片。
        OH_ArkUI_NativeModule_ImageCollectionDestroy(collection);
        return;
    }
    napi_env env = request->env;
    napi_handle_scope scope = nullptr;
    if (napi_open_handle_scope(env, &scope) != napi_ok) {
        OH_ArkUI_NativeModule_ImageCollectionDestroy(collection);
        delete request;
        return;
    }
    napi_value result = nullptr;
    napi_value items = nullptr;
    bool built = napi_create_object(env, &result) == napi_ok &&
        napi_create_array(env, &items) == napi_ok;
    if (built) {
        uint32_t count = 0;
        for (int32_t nodeId : request->nodeIds) {
            OH_PixelmapNative* pixelmap = nullptr;
            // 集合为空表示本次请求没有产生任何结果项，无法取出。
            ArkUI_ErrorCode itemError = collection == nullptr ? overallError : ARKUI_ERROR_CODE_NO_ERROR;
            const ArkUI_ErrorCode takeError = collection == nullptr ? overallError :
                OH_ArkUI_NativeModule_ImageCollectionTakeItemByNodeId(collection, nodeId, &pixelmap, &itemError);
            napi_value item = ImageItem(env, nodeId, takeError, itemError, pixelmap);
            if (pixelmap != nullptr) {
                // 取出时所有权已转移到此处，上面的转换已完成。
                OH_PixelmapNative_Destroy(&pixelmap);
            }
            if (item != nullptr) {
                napi_set_element(env, items, count, item);
                count += 1;
            }
        }
        built = NumberProperty(env, result, "submitError", 0) &&
            NumberProperty(env, result, "overallError", static_cast<int32_t>(overallError)) &&
            napi_set_named_property(env, result, "items", items) == napi_ok;
    }
    if (built) {
        napi_resolve_deferred(env, request->deferred, result);
    } else {
        napi_value error = nullptr;
        if (napi_create_string_utf8(env, "image result bridge failed", NAPI_AUTO_LENGTH, &error) == napi_ok) {
            napi_reject_deferred(env, request->deferred, error);
        }
    }
    OH_ArkUI_NativeModule_ImageCollectionDestroy(collection);
    napi_close_handle_scope(env, scope);
    delete request;
}
```

取出过程中的关键处理如下。

- collection为NULL表示本次请求没有可用的结果集合（上下文失效或集合分配失败），此时直接按整体错误码处理，不要调用取出接口。
- 取出的PixelMap在转换成ArkTS对象后立即释放，避免在回调中持有native对象跨出本次回调。
- 无论取出是否全部成功，回调结束前都销毁集合，释放未被取出的PixelMap。
- 页面可能已经退出，回调仍然会执行。示例的回调只做结果转换与清理，不访问页面状态；页面侧用active标记判断页面是否仍然存在，已退出时丢弃结果，见[在页面上展示结果](#在页面上展示结果)。

### 在页面上展示结果

结果项被转换成ArkTS对象后交给页面渲染。示例的桥接结果包含受理结果、整体结果和结果项数组，每个结果项包含节点ID、取出结果、单项错误码、像素尺寸和可选的PixelMap。

<!-- @[ndk_image_result_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection/entry/src/main/cpp/types/libentry/Index.d.ts) -->

``` TypeScript
export interface ImageItemResult {
  // 本结果项的节点ID。每个请求的节点ID都有一项，失败项也包含在内。
  nodeId: number;
  // 从集合中取出该项的结果。0表示取出成功。
  takeError: number;
  // 该节点图片的采集结果。非0表示该项没有图片。
  itemError: number;
  // 图片的像素尺寸。该项没有图片时这两个字段不存在。
  width?: number;
  height?: number;
  // 采集到的图片。示例在此不释放，对象由ArkTS持有。
  pixelMap?: image.PixelMap;
}

export interface ImageCollectionResult {
  // 请求的受理结果。非0表示请求被拒绝，没有任何结果项。
  submitError: number;
  // 回调上报的整体结果。部分失败时仍会返回全部结果项。
  // 请求被拒绝时不会执行回调，此处与submitError相同。
  overallError: number;
  items: ImageItemResult[];
}
```

页面在调用采集前读取节点ID，拿到结果后按请求顺序渲染每一项。示例用active标记页面是否仍然存在，页面退出后不再修改状态。

<!-- @[ndk_image_page_collect](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection/entry/src/main/ets/pages/ImagePage.ets) -->

``` TypeScript
private async capture(nodeIds: number[]): Promise<void> {
  if (this.busy) {
    return;
  }
  this.busy = true;
  this.status = 'pending';
  hilog.info(DOMAIN, TAG, 'collectImages begin, nodes=%{public}d', nodeIds.length);
  try {
    const result: ImageCollectionResult = await nativeUi.collectImages(nodeIds);
    if (!this.active) {
      return;
    }
    this.items = result.items;
    this.status = `submitError=${result.submitError}; overallError=${result.overallError}; ` +
      `items=${result.items.length}`;
    hilog.info(DOMAIN, TAG, 'collectImages done, submitError=%{public}d, overallError=%{public}d, items=%{public}d',
      result.submitError, result.overallError, result.items.length);
  } catch (error) {
    const reason: string = failure(error);
    if (this.active) {
      this.status = reason;
      hilog.error(DOMAIN, TAG, 'collectImages failed, reason=%{public}s', reason);
    }
  } finally {
    if (this.active) {
      this.busy = false;
    }
  }
}
```

### 接口返回示例

示例工程把受理结果、整体结果与结果项数量放在同一行状态中显示。下表列出页面中三个场景的实际返回。

| 场景 | 请求 | 页面返回 |
|---|---|---|
| 单个Image节点 | 1个节点ID | 返回1个结果项，尺寸为640×480。 |
| 三个节点 | Image节点与两个Text节点各1个 | 返回3个结果项，按请求顺序展示，都有图片。 |
| 含已移除节点 | Image节点与一个已移除节点的节点ID | 返回2个结果项，已移除节点的结果项没有图片，其余正常。 |

示例桥接返回submitError、overallError和items三个字段，其中submitError表示请求是否被受理，overallError表示这一批的总体结果，items按请求顺序给出每个节点的结果项。请求被拒绝时items为空数组。

示例返回中的错误码含义与取值见[ArkUI_ErrorCode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)。

### 采集页面文本

[OH_ArkUI_NativeModule_UIAgentGetPageText](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagentgetpagetext)必须在目标UI实例的UI线程上同步调用（在非目标UI线程调用会导致进程终止）。以下示例由ArkTS页面上的UI事件（如按钮点击）直接触发，从而保证当前处于目标UI线程。获取目标页面的`ArkUI_ContextHandle`后调用采集接口，读取JSON字符串后需调用[OH_ArkUI_NativeModule_UIJsonWrapperDestroy](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy)释放封装对象。

<!-- @[ui_agent_get_page_text](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIAgentGetPageText/Library/src/main/cpp/napi_init.cpp) -->

``` C++
napi_value GetPageText(napi_env env, napi_callback_info info)
{
    size_t argc = 1;
    napi_value argv[1] = {nullptr};
    void *data = nullptr;
    if (napi_get_cb_info(env, info, &argc, argv, nullptr, &data) != napi_ok || argc != 1 || data == nullptr) {
        return ThrowError(env, ARKUI_ERROR_CODE_PARAM_INVALID, "Pass the current page's UIContext.");
    }
    ArkUI_ContextHandle context = nullptr;
    int32_t code = GetContext(env, argv[0], *static_cast<ContextCache *>(data), context);
    if (code != ARKUI_ERROR_CODE_NO_ERROR || context == nullptr) {
        return ThrowError(env, code != ARKUI_ERROR_CODE_NO_ERROR ? code : ARKUI_ERROR_CODE_UI_CONTEXT_INVALID,
            "Cannot obtain the native UI context.");
    }

    // Call synchronously from an ArkUI event on the UI thread, never from a worker/async task.
    OH_ArkUI_NativeModule_UIJsonWrapper *pageText = nullptr;
    code = OH_ArkUI_NativeModule_UIAgentGetPageText(context, &pageText);
    JsonOwner ownedText(pageText, OH_ArkUI_NativeModule_UIJsonWrapperDestroy);
    if (code != ARKUI_ERROR_CODE_NO_ERROR) {
        return ThrowError(env, code, "OH_ArkUI_NativeModule_UIAgentGetPageText failed.");
    }
    const char *jsonData = OH_ArkUI_NativeModule_UIJsonWrapperGetData(ownedText.get());
    if (jsonData == nullptr) {
        return ThrowError(env, ARKUI_ERROR_CODE_INTERNAL_ERROR, "The collected JSON is unavailable.");
    }
    uint32_t size = OH_ArkUI_NativeModule_UIJsonWrapperGetSize(ownedText.get());
    napi_value result = nullptr;
    // N-API copies the UTF-8 bytes before the owning wrapper is destroyed on function exit.
    if (napi_create_string_utf8(env, jsonData, size, &result) != napi_ok) {
        return ThrowError(env, ARKUI_ERROR_CODE_INTERNAL_ERROR, "Cannot copy the collected JSON to ArkTS.");
    }
    OH_LOG_Print(LOG_APP, LOG_INFO, SAMPLE_DOMAIN, SAMPLE_TAG, "Collection succeeded, bytes=%{public}u", size);
    return result;
}
```

在ArkTS侧解析返回的JSON字符串：

<!-- @[ui_page_text_parse](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIAgentGetPageText/Library/src/main/ets/PageText.ets) -->

``` TypeScript
export interface PageTextItem {
  // Native node id; this is different from the ArkTS component's .id('sampleText').
  id: number;
  // [x, y, width, height] in physical pixels, relative to the target window.
  rect: number[];
  content: string;
}

export interface PageTextResult {
  schemaVersion: number;
  texts: PageTextItem[];
}

/** Parse the versioned JSON returned by the native page text API. */
export function parsePageText(json: string): PageTextResult {
  const result: PageTextResult = JSON.parse(json) as PageTextResult;
  if (result.schemaVersion !== 1 || !Array.isArray(result.texts)) {
    throw new Error('Unsupported page text schema');
  }
  return result;
}
```

## 常见问题

以下汇总节点图片采集过程中的常见问题。错误码的定义与取值见[ArkUI_ErrorCode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)。

### 为什么整个采集没有返回图片

返回[ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)时，本次采集没有可用结果。提交时出现，请在当前页面重新获取上下文句柄后重试；回调中出现，说明页面已退出或实例已销毁，按页面的有效标记丢弃本次结果。

### 为什么某个节点没有图片

结果项没有图片、其错误码为[ARKUI_ERROR_CODE_NODE_NOT_FOUND](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)时，说明该节点ID已失效。提交前重新读取节点ID且不缓存；需要采集可能被移除的节点时，把节点仍然存在作为采集前提；同一批次中的其他结果项仍可正常使用。

### 为什么只有部分节点取到图片

部分结果项没有图片、整体错误码为[ARKUI_ERROR_CODE_COLLECTION_PARTIAL_FAILED](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)时，其余结果项仍可正常使用。逐项取出并检查各结果项，只对失败项做补偿，不要丢弃已经成功的结果。

### 为什么连续提交时后一次被拒绝

提交被拒绝、返回[ARKUI_ERROR_CODE_COMMAND_UNFINISHED](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)时，说明上一次请求的回调还没有返回。提交后禁用触发采集的交互，收到回调并处理完结果后再恢复，不要用循环提交的方式重试。

### 为什么提交被拒绝且没有回调

提交被拒绝且没有回调时，按返回值定位原因：节点ID数量不在1到20之间返回[ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGE](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)，节点ID重复返回[ARKUI_ERROR_CODE_DUPLICATE_NODE_ID](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)；节点ID数组为空、回调为空或上下文无效时同样会被拒绝。提交前对节点ID去重并检查数量，超过20个节点时分批提交。示例桥接在提交前校验数量范围，越界时抛出ArkTS异常。

### 为什么采到的图片尺寸与页面显示不一致

Image节点能取到源图时，采集结果是组件的完整源图，像素尺寸由源图决定，与页面显示尺寸无关（示例源图为640×480，页面显示为96vp）；取不到源图时按节点边界截取。其他节点统一按节点边界截取，尺寸随显示尺寸变化。按源图尺寸处理业务，需要与显示尺寸一致时由应用自行缩放，不要用采集结果反推布局。

### 为什么某个节点采集超时

某个结果项没有图片、其错误码为[ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_TIMEOUT](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)时，说明该节点截图超时，同一批次的其他结果项不受影响。记录节点ID与当时的界面状态，在业务允许时重新发起一次请求，不要在同一个批次内对超时项循环重试。

### 为什么长时间采集后内存持续增长

常见原因是只取了PixelMap而没有释放，或把结果集合跨回调保存而没有销毁；PixelMap与集合是两层所有权，只释放其中一层仍会保留另一层的内存。取出的PixelMap在转换或使用完成后调用[OH_PixelmapNative_Destroy](../reference/apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_destroy)释放，回调结束前销毁集合，不要在页面状态中长期保存集合指针。

### 页面退出后收到回调怎么办

请求受理后，回调和桥接结果仍可能在页面退出之后到达，例如采集过程中返回上一页，此时访问已销毁的页面状态会导致异常。在页面生命周期中维护有效标记，结果到达时检查该标记，页面已退出时只做清理、不修改界面状态，并释放PixelMap与销毁集合。

### 页面文本采集返回错误或内存泄漏怎么办

调用[OH_ArkUI_NativeModule_UIAgentGetPageText](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagentgetpagetext)时，若上下文无效会返回[ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)；若页面存在但没有符合条件的文本，接口会正常返回空的`texts`数组（`{"schemaVersion":1,"texts":[]}`）；若发生采集或JSON序列化失败等内部错误，则会返回[ARKUI_ERROR_CODE_INTERNAL_ERROR](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)。调用成功时，必须确保在读取完JSON字符串后调用[OH_ArkUI_NativeModule_UIJsonWrapperDestroy](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy)释放对象，且不要在销毁后继续使用`OH_ArkUI_NativeModule_UIJsonWrapperGetData`返回的指针。
