# ui_info_collection.h

## 概述

声明供应用内智能体和UI自动化使用的接口，用于监听UI交互事件并获取命中的节点。<br> 返回状态码的函数通过ArkUI_ErrorCode报告错误，异步执行结果通过相应的完成回调报告。 这些接口不使用errno传递错误；调用后的errno值未定义，不得用它判断调用是否成功。

**引用文件：** <arkui/ui_info_collection.h>

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) | OH_ArkUI_NativeModule_UIAgentTreeRequest | 声明UI树采集请求结构体。 |
| [OH_ArkUI_NativeModule_UIContentChangeEvent](capi-arkui-nativemodule-oh-arkui-nativemodule-uicontentchangeevent.md) | OH_ArkUI_NativeModule_UIContentChangeEvent | 声明ArkUI内容变化事件结构体。 |
| [OH_ArkUI_NativeModule_ImageCollection](capi-arkui-nativemodule-oh-arkui-nativemodule-imagecollection.md) | OH_ArkUI_NativeModule_ImageCollection | 声明ArkUI图像采集结果结构体。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_ArkUI_NativeModule_UIInfoCollection_InteractionEventType](#oh_arkui_nativemodule_uiinfocollection_interactioneventtype) | OH_ArkUI_NativeModule_UIInfoCollection_InteractionEventType | 定义可监听的UI交互事件类型。<br> 各枚举值均为位标志，用于构造传给 [OH_ArkUI_NativeModule_UIInfoCollectionRegisterInteractionObserver](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectionregisterinteractionobserver)的eventMask。 |
| [OH_ArkUI_NativeModule_UIAgentTreeType](#oh_arkui_nativemodule_uiagenttreetype) | OH_ArkUI_NativeModule_UIAgentTreeType | 定义UI树采集类型的枚举。 |
| [OH_ArkUI_NativeModule_UIContentChangeEventCategory](#oh_arkui_nativemodule_uicontentchangeeventcategory) | OH_ArkUI_NativeModule_UIContentChangeEventCategory | 定义UI内容变化事件类别的枚举。 |
| [OH_ArkUI_NativeModule_UIContentChangeIgnoreType](#oh_arkui_nativemodule_uicontentchangeignoretype) | OH_ArkUI_NativeModule_UIContentChangeIgnoreType | 定义可忽略的UI内容变化事件类型。 |
| [OH_ArkUI_NativeModule_UIContentChangeEventType](#oh_arkui_nativemodule_uicontentchangeeventtype) | OH_ArkUI_NativeModule_UIContentChangeEventType | 定义ArkUI状态变化事件类型的枚举。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback)(const OH_ArkUI_NativeModule_UIJsonWrapper *json, void *userData)](#oh_arkui_nativemodule_uiinfocollectioninteractionjsoncallback) | OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback | 定义接收感知到的交互事件的回调类型。<br> 回调通过借用的[OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md)对象接收事件数据， 不取得该对象的所有权。对象仅在本次回调执行期间有效，回调不得保留或销毁该对象。 事件数据中的所有位置坐标均相对于屏幕（显示器），单位为物理像素（px）。 事件数据顶层始终包含schemaVersion字段。 顶层结构为{ "schemaVersion": 1, "type": "<event type>", ... }。<br> 各事件类型对应的字段见下方列表。 - 点击手势或点击事件：id、point、count、fingers。 - 长按手势：id、point、actualDuration（毫秒）、action（"end"）。 - 拖动手势：id、point、direction、action（"start" \| "end" \| "cancel"）。 - 捏合手势：id、point（由[x, y]组成的数组）、fingers、action（"start" \| "end" \| "cancel"）； 仅在"end"时包含scale字段。 - 旋转手势：id、point（由[x, y]组成的数组）、fingers、action（"start" \| "end" \| "cancel"）； 仅在"end"时包含angle字段，单位为度。 - 滑动手势：id、downPoint（由[x, y]组成的数组）、upPoint（由[x, y]组成的数组）、 direction、speed、actualSpeed。 - 拖拽事件：action（"start" \| "end"）；"start"时包含id、point、hostName、actualDuration； "end"时包含point、dropResult（"success" \| "fail"）、id（目标节点ID，仅在成功时包含）、hostName。 - 触摸事件：action（"down" \| "up"）、fingerId、point；"down"时还包含id（命中节点ID）。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIInfoCollectionRegisterInteractionObserver(ArkUI_ContextHandle uiContext, uint32_t eventMask, uint32_t *registerID, OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback callback, void *userData)](#oh_arkui_nativemodule_uiinfocollectionregisterinteractionobserver) | - | 注册UI交互事件观察者。<br> 观察者仅接收eventMask指定类型的事件回调。同一个UI实例可以注册多个观察者。 使用相同的callback和userData组合重复注册，会创建一个新的独立观察者，并分配新的注册ID。<br> 不再使用观察者时，必须调用[OH_ArkUI_NativeModule_UIInfoCollectionUnregisterInteractionObserver](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectionunregisterinteractionobserver) 注销回调。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIInfoCollectionUnregisterInteractionObserver(uint32_t registerID)](#oh_arkui_nativemodule_uiinfocollectionunregisterinteractionobserver) | - | 注销交互事件观察者。<br> 本次调用完成后，不再调用对应的回调函数。<br> 本函数是线程安全的，可以从任意线程调用，且不会阻塞调用方，但不具备异步信号安全性。 |
| [typedef void (\*OH_ArkUI_NativeModule_UIAgentJsonCallback)(ArkUI_ContextHandle context, uint64_t requestId, ArkUI_ErrorCode errorCode, OH_ArkUI_NativeModule_UIJsonWrapper *json, void *userData)](#oh_arkui_nativemodule_uiagentjsoncallback) | OH_ArkUI_NativeModule_UIAgentJsonCallback | 定义异步JSON树采集请求完成时调用的回调函数类型。<br> 每个被接受的请求均在UI线程上触发且仅触发一次回调。 仅当errorCode为ARKUI_ERROR_CODE_NO_ERROR时，回调才会接收非NULL的JSON对象并取得其所有权。 调用方必须调用OH_ArkUI_NativeModule_UIJsonWrapperDestroy释放该对象。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestCreate(OH_ArkUI_NativeModule_UIAgentTreeType treeType, OH_ArkUI_NativeModule_UIAgentTreeRequest **request)](#oh_arkui_nativemodule_uiagenttreerequestcreate) | - | 创建UI树采集请求。 |
| [void OH_ArkUI_NativeModule_UIAgentTreeRequestDestroy(OH_ArkUI_NativeModule_UIAgentTreeRequest *request)](#oh_arkui_nativemodule_uiagenttreerequestdestroy) | - | 销毁UI树采集请求对象。<br> 传入NULL时不执行任何操作。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetFilterPureLayoutNodes(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)](#oh_arkui_nativemodule_uiagenttreerequestsetfilterpurelayoutnodes) | - | 设置是否从返回的UI树中过滤纯布局节点。<br> 默认不启用过滤。启用后，被过滤节点下仍需保留的后代节点会挂载到最近的、仍被保留的祖先节点， 并保持原有的相对顺序。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetFilterOccludedNodes(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)](#oh_arkui_nativemodule_uiagenttreerequestsetfilteroccludednodes) | - | 设置是否从返回的UI树中过滤被完全遮挡的节点。<br> 默认不启用过滤，且仅可对可见树采集请求启用此选项。开启遮挡过滤可能给采集带来较大的额外计算量，请根据界面复杂程度酌情使用。 关闭此选项不会关闭可见性过滤、裁剪过滤、离屏节点过滤或完全透明节点过滤。<br> 作为遮挡方的节点所需满足的不透明度阈值由 [OH_ArkUI_NativeModule_UIAgentTreeRequestSetOcclusionOpacityThreshold](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreerequestsetocclusionopacitythreshold)单独配置。 修改此选项不会改变该阈值。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetOcclusionOpacityThreshold(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, float threshold)](#oh_arkui_nativemodule_uiagenttreerequestsetocclusionopacitythreshold) | - | 设置节点作为遮挡方参与遮挡判断时，其最终不透明度必须达到的最小值。<br> 默认值为1.0，仅可见树采集请求支持此选项。 只有满足阈值条件的遮挡节点的区域并集完全覆盖目标节点的有效可见区域时，才会移除目标节点。<br> 如果未通过[OH_ArkUI_NativeModule_UIAgentTreeRequestSetFilterOccludedNodes](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreerequestsetfilteroccludednodes)启用遮挡过滤， 此阈值不会生效。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetInteractionInfo(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)](#oh_arkui_nativemodule_uiagenttreerequestsetinteractioninfo) | - | 设置是否采集额外的交互信息。<br> 默认不启用采集。启用后，结果中会包含受支持的交互信息，例如节点是否可点击、可获焦或可编辑。 此选项不会注册事件观察者，也不会改变任何节点的交互行为。<br> 关闭此选项不会移除默认精简结果中已有的字段。 高级属性采集不会隐式启用此选项，也不会采集此选项专属的字段。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetAccessibilityInfo(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)](#oh_arkui_nativemodule_uiagenttreerequestsetaccessibilityinfo) | - | 设置是否采集额外的无障碍信息。<br> 默认不启用采集。启用后，结果中会包含受支持的无障碍信息，例如无障碍内容。 此选项不会启用无障碍服务，也不会改变节点行为。<br> 关闭此选项不会移除默认精简结果中已有的字段。 高级属性采集不会隐式启用此选项，也不会采集此选项专属的字段。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetCollectVisualProperties(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)](#oh_arkui_nativemodule_uiagenttreerequestsetcollectvisualproperties) | - | 设置是否采集高级视觉属性。<br> 默认不启用采集。启用后，结果中会额外包含受支持的、用于描述可直接感知的外观的属性， 例如视觉样式和显示状态。<br> 默认精简结果中已有的属性不会重复采集。无论交互信息和无障碍信息采集选项是否启用， 这两类信息的专属字段均不属于本组属性。内部诊断属性始终不会包含在内。<br> 此选项独立于高级功能属性采集选项，不会改变UI树中保留的节点。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetCollectFunctionalProperties(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)](#oh_arkui_nativemodule_uiagenttreerequestsetcollectfunctionalproperties) | - | 设置是否采集高级功能属性。<br> 默认不启用采集。启用后，结果中会额外包含受支持的属性，用于描述开发者配置的组件行为和功能能力。<br> 默认精简结果中已有的属性不会重复采集。无论交互信息和无障碍信息采集选项是否启用， 这两类信息的专属字段均不属于本组属性。内部诊断属性始终不会包含在内。<br> 此选项独立于高级视觉属性采集选项，不会改变UI树中保留的节点。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentGetTreeJson(ArkUI_ContextHandle context, const OH_ArkUI_NativeModule_UIAgentTreeRequest *request, OH_ArkUI_NativeModule_UIJsonFormat format, OH_ArkUI_NativeModule_UIJsonWrapper **json)](#oh_arkui_nativemodule_uiagentgettreejson) | - | 同步采集UI树，并以JSON格式返回。<br> 本函数必须在UI线程上调用。结果最多包含5000个节点，大小不得超过5 MiB。 大小限制以规范的紧凑格式JSON为准；如果带缩进和换行的格式化输出本身超过5 MiB，请求同样失败。 不会返回部分JSON数据。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentGetTreeJsonAsync(ArkUI_ContextHandle context, const OH_ArkUI_NativeModule_UIAgentTreeRequest *request, OH_ArkUI_NativeModule_UIJsonFormat format, OH_ArkUI_NativeModule_UIAgentJsonCallback callback, void *userData, uint64_t *requestId)](#oh_arkui_nativemodule_uiagentgettreejsonasync) | - | 发起异步UI树采集请求，并通过异步回调接收采集结果。<br> 本函数必须在UI线程上调用。函数返回前会复制request和format， 因此调用方可以在调用返回后立即销毁或复用请求对象。 每个被接受的请求都在UI线程上完成，且仅完成一次。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentGetPageText(ArkUI_ContextHandle uiContext, OH_ArkUI_NativeModule_UIJsonWrapper** pageText)](#oh_arkui_nativemodule_uiagentgetpagetext) | - | 同步采集当前ArkUI页面的文本，并以JSON格式输出。<br> 每个JSON项包含用于标识控件的整数"id"、相对于目标窗口的矩形区域"rect"， 以及表示文本内容的字符串"content"。 使用完毕后，必须调用OH_ArkUI_NativeModule_UIJsonWrapperDestroy释放结果所占用的内存。 本函数必须在UI线程上调用。 |
| [typedef void (\*OH_ArkUI_NativeModule_UIContentChangeEventCallback)(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, void* userData)](#oh_arkui_nativemodule_uicontentchangeeventcallback) | OH_ArkUI_NativeModule_UIContentChangeEventCallback | 定义已注册的ArkUI状态变化事件触发时调用的回调函数类型。<br> 回调在注册时指定的UI上下文所关联的UI线程上执行。 事件快照不可修改，且仅在本次回调返回前有效。 ArkUI仅借用userData，不取得其所有权，也不会访问或释放其指向的数据。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_RegisterUIContentChangeEvent(ArkUI_ContextHandle uiContext, bool withStart, uint32_t eventMask, uint32_t ignoreMask, void* userData, OH_ArkUI_NativeModule_UIContentChangeEventCallback callback, uint64_t* subscriptionId)](#oh_arkui_nativemodule_registeruicontentchangeevent) | - | 为指定UI上下文注册所选类别的ArkUI状态变化事件订阅。<br> 每次成功调用都会创建一个独立订阅。返回的订阅ID非零，且在该UI上下文内唯一。 回调在该UI上下文关联的UI线程上同步执行。 ArkUI仅借用uiContext和userData，不会释放两者。操作失败时，不修改subscriptionId指向的值。 本函数必须在UI线程上调用；从非UI线程调用会导致进程终止。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UnRegisterUIContentChangeEvent(ArkUI_ContextHandle uiContext, uint64_t subscriptionId)](#oh_arkui_nativemodule_unregisteruicontentchangeevent) | - | 注销指定UI上下文中仍然有效的ArkUI状态变化事件订阅。<br> 本函数成功返回后，后续事件将不再触发已移除订阅的回调，调用方随后可以释放其userData。 在回调中取消订阅，不会改变当前正在分发的这一批回调。 本函数必须在UI线程上调用；从非UI线程调用会导致进程终止。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIContentChangeEventGetType(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, OH_ArkUI_NativeModule_UIContentChangeEventType* type)](#oh_arkui_nativemodule_uicontentchangeeventgettype) | - | 从ArkUI状态变化事件快照中获取事件类型。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIContentChangeEventGetTimestamp(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, uint64_t* nanoTimestamp)](#oh_arkui_nativemodule_uicontentchangeeventgettimestamp) | - | 获取ArkUI状态变化事件快照的单调时间戳。<br> 该时间戳在事件完成时记录，单位为纳秒，使用单调时钟，不表示日历时间。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIContentChangeEventGetContext(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, ArkUI_ContextHandle* uiContext)](#oh_arkui_nativemodule_uicontentchangeeventgetcontext) | - | 获取与ArkUI状态变化事件快照关联的UI上下文。<br> 返回的句柄为借用句柄，调用方不拥有其所有权，不得释放该句柄，也不得在回调返回后使用该句柄。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIContentChangeEventGetContentChangeEventJson(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, const OH_ArkUI_NativeModule_UIJsonWrapper** json)](#oh_arkui_nativemodule_uicontentchangeeventgetcontentchangeeventjson) | - | 从ArkUI状态变化事件快照中获取内容变化事件详情，并以JSON封装对象返回。<br> JSON输出的顶层包含schemaVersion字段，并包含内容变化类型、触发节点、目标节点、浮层类型， 以及根据事件类别决定是否包含的子树转储信息。<br> 页面事件标识目标页面，滚动事件标识发生滚动的节点，浮层事件标识浮层节点并提供浮层类型，例如"dialog"。 触发节点是引起内容变化的节点，在浮层事件和一般的开始、结束场景中可用。 对于页面事件和滚动事件，如果无法提供触发节点，则该节点为NULL。 如果无法提供目标节点，操作仍然成功，返回的JSON中仍包含schemaVersion字段。 JSON封装对象中引用的句柄均为借用句柄，不得释放，也不得在回调返回后使用。 |
| [typedef void (\*OH_ArkUI_NativeModule_ImageCollectionCallback)(ArkUI_ErrorCode errorCode, OH_ArkUI_NativeModule_ImageCollection* collection, void* userData)](#oh_arkui_nativemodule_imagecollectioncallback) | OH_ArkUI_NativeModule_ImageCollectionCallback | 定义用于返回ArkUI节点图像采集结果的回调函数类型。<br> 对于每个被接受的请求，框架都会在UI线程上调用且仅调用一次此回调。 当<b>errorCode</b>为ARKUI_ERROR_CODE_NO_ERROR时，框架将非<b>NULL</b>的 <b>collection</b>的所有权转移给调用方。当<b>errorCode</b>为 ARKUI_ERROR_CODE_INTERNAL_ERROR或ARKUI_ERROR_CODE_UI_CONTEXT_INVALID时， <b>collection</b>为<b>NULL</b>。<br> 框架将<b>userData</b>原样传回，不会解引用该指针，也不会复制或释放其指向的对象。 调用方必须保证该对象在回调结束使用前一直有效。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_GetImagesByNodeIdAsync(ArkUI_ContextHandle context, const int32_t* nodeIds, uint32_t count, OH_ArkUI_NativeModule_ImageCollectionCallback callback, void* userData)](#oh_arkui_nativemodule_getimagesbynodeidasync) | - | 异步采集指定ArkUI节点ID对应的图像。<br> 单次请求可包含<b>1</b>到<b>20</b>个互不重复的节点ID。 框架会在本函数返回前复制<b>nodeIds</b>数组。 如果<b>count</b>为<b>0</b>或大于<b>20</b>，本函数返回 ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGE。<br> 每个被接受的节点ID在结果集合中都有对应的结果项，即使未找到该节点或无法截取其图像。 对于<b>Image</b>节点，如果可以获取其源<b>PixelMap</b>，则返回完整的源<b>PixelMap</b>； 否则，对节点边界内的渲染内容进行截图。非<b>Image</b>节点同样对节点边界内的渲染内容进行截图。 节点无需处于可见状态。<br> 如果找不到请求的节点ID对应的ArkUI节点，对应结果项会报告 <b>ARKUI_ERROR_CODE_NODE_NOT_FOUND</b>，调用方应检查节点ID。 截图超时时，对应结果项报告<b>ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_TIMEOUT</b>，调用方可以重试请求。 发生其他内部截图错误时，对应结果项报告<b>ARKUI_ERROR_CODE_INTERNAL_ERROR</b>， 调用方可以在处理该错误后重试请求。单个结果项失败不会改变请求整体成功的结果。<br> 调用方可以从任意线程调用本函数。对于每个被接受的请求， 框架都会在<b>context</b>关联的UI线程上调用且仅调用一次<b>callback</b>。 如果上一次请求尚未完成，本函数返回ARKUI_ERROR_CODE_COMMAND_UNFINISHED。 调用方必须等待该请求完成后再提交下一次请求。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImageCollectionTakeItemByNodeId(OH_ArkUI_NativeModule_ImageCollection* collection, int32_t nodeId, OH_PixelmapNative** outPixelmap, ArkUI_ErrorCode* outItemError)](#oh_arkui_nativemodule_imagecollectiontakeitembynodeid) | - | 取出指定节点ID对应的结果。<br> 对于图像采集成功的结果项，本函数将<b>PixelMap</b>的所有权转移给调用方。 调用方必须调用<b>OH_PixelmapNative_Destroy</b>释放该对象。 本函数也可取出图像采集失败的结果项，此时会将<b>*outPixelmap</b>设置为<b>NULL</b>， 并将该结果项的错误码写入<b>*outItemError</b>。集合中每个节点ID对应的结果仅可取出一次。<br> 销毁集合时，仅释放调用方尚未取出的<b>PixelMap</b>实例， 已转移给调用方的<b>PixelMap</b>不会因此失效。<br> 调用方不得针对同一个集合，将本函数与其他集合操作接口并发调用。 |
| [void OH_ArkUI_NativeModule_ImageCollectionDestroy(OH_ArkUI_NativeModule_ImageCollection* collection)](#oh_arkui_nativemodule_imagecollectiondestroy) | - | 销毁图像集合，并释放尚未取出的<b>PixelMap</b>实例。<br> 调用方必须销毁回调返回的每个非<b>NULL</b>集合，即使其中的所有结果项均已取出。 本函数不会释放通过<b>OH_ArkUI_NativeModule_ImageCollectionTakeItemByNodeId</b> 取得的<b>PixelMap</b>实例，也不会使这些实例失效。<br> 调用方不得针对同一个集合，将本函数与其他集合操作接口并发调用。 |

### 变量

| 名称 | 描述 |
| -- | -- |
| void (*OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback)( const OH_ArkUI_NativeModule_UIJsonWrapper *json, void *userData) | 定义接收感知到的交互事件的回调类型。<br> 回调通过借用的[OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md)对象接收事件数据， 不取得该对象的所有权。对象仅在本次回调执行期间有效，回调不得保留或销毁该对象。 事件数据中的所有位置坐标均相对于屏幕（显示器），单位为物理像素（px）。 事件数据顶层始终包含schemaVersion字段。 顶层结构为{ "schemaVersion": 1, "type": "<event type>", ... }。<br> 各事件类型对应的字段见下方列表。 - 点击手势或点击事件：id、point、count、fingers。 - 长按手势：id、point、actualDuration（毫秒）、action（"end"）。 - 拖动手势：id、point、direction、action（"start" \| "end" \| "cancel"）。 - 捏合手势：id、point（由[x, y]组成的数组）、fingers、action（"start" \| "end" \| "cancel"）； 仅在"end"时包含scale字段。 - 旋转手势：id、point（由[x, y]组成的数组）、fingers、action（"start" \| "end" \| "cancel"）； 仅在"end"时包含angle字段，单位为度。 - 滑动手势：id、downPoint（由[x, y]组成的数组）、upPoint（由[x, y]组成的数组）、 direction、speed、actualSpeed。 - 拖拽事件：action（"start" \| "end"）；"start"时包含id、point、hostName、actualDuration； "end"时包含point、dropResult（"success" \| "fail"）、id（目标节点ID，仅在成功时包含）、hostName。 - 触摸事件：action（"down" \| "up"）、fingerId、point；"down"时还包含id（命中节点ID）。<br>**起始版本：** 26.2.0<br>**系统能力：** SystemCapability.ArkUI.ArkUI.Full |
| void (*OH_ArkUI_NativeModule_UIAgentJsonCallback)(ArkUI_ContextHandle context, uint64_t requestId, ArkUI_ErrorCode errorCode, OH_ArkUI_NativeModule_UIJsonWrapper *json, void *userData) | 定义异步JSON树采集请求完成时调用的回调函数类型。<br> 每个被接受的请求均在UI线程上触发且仅触发一次回调。 仅当errorCode为ARKUI_ERROR_CODE_NO_ERROR时，回调才会接收非NULL的JSON对象并取得其所有权。 调用方必须调用OH_ArkUI_NativeModule_UIJsonWrapperDestroy释放该对象。<br>**起始版本：** 26.2.0<br>**系统能力：** SystemCapability.ArkUI.ArkUI.Full |
| void (*OH_ArkUI_NativeModule_UIContentChangeEventCallback)( const OH_ArkUI_NativeModule_UIContentChangeEvent* event, void* userData) | 定义已注册的ArkUI状态变化事件触发时调用的回调函数类型。<br> 回调在注册时指定的UI上下文所关联的UI线程上执行。 事件快照不可修改，且仅在本次回调返回前有效。 ArkUI仅借用userData，不取得其所有权，也不会访问或释放其指向的数据。<br>**起始版本：** 26.2.0<br>**系统能力：** SystemCapability.ArkUI.ArkUI.Full |
| void (*OH_ArkUI_NativeModule_ImageCollectionCallback)(ArkUI_ErrorCode errorCode, OH_ArkUI_NativeModule_ImageCollection* collection, void* userData) | 定义用于返回ArkUI节点图像采集结果的回调函数类型。<br> 对于每个被接受的请求，框架都会在UI线程上调用且仅调用一次此回调。 当<b>errorCode</b>为ARKUI_ERROR_CODE_NO_ERROR时，框架将非<b>NULL</b>的 <b>collection</b>的所有权转移给调用方。当<b>errorCode</b>为 ARKUI_ERROR_CODE_INTERNAL_ERROR或ARKUI_ERROR_CODE_UI_CONTEXT_INVALID时， <b>collection</b>为<b>NULL</b>。<br> 框架将<b>userData</b>原样传回，不会解引用该指针，也不会复制或释放其指向的对象。 调用方必须保证该对象在回调结束使用前一直有效。<br>**起始版本：** 26.2.0<br>**系统能力：** SystemCapability.ArkUI.ArkUI.Full |

## 枚举类型说明

### OH_ArkUI_NativeModule_UIInfoCollection_InteractionEventType

```c
enum OH_ArkUI_NativeModule_UIInfoCollection_InteractionEventType
```

**描述：**

定义可监听的UI交互事件类型。<br> 各枚举值均为位标志，用于构造传给 [OH_ArkUI_NativeModule_UIInfoCollectionRegisterInteractionObserver](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectionregisterinteractionobserver)的eventMask。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_NONE = 0 | 无事件。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_TAP = 1 << 0 | 点击手势。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_CLICK = 1 << 1 | 点击事件。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_LONG_PRESS = 1 << 2 | 长按手势。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_PAN = 1 << 3 | 拖动手势。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_PINCH = 1 << 4 | 捏合手势。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_ROTATION = 1 << 5 | 旋转手势。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_SWIPE = 1 << 6 | 滑动手势。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_DRAG = 1 << 7 | 统一拖拽事件。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_TOUCH = 1 << 8 | 原始触摸按下或抬起事件。<br>**起始版本：** 26.2.0 |

### OH_ArkUI_NativeModule_UIAgentTreeType

```c
enum OH_ArkUI_NativeModule_UIAgentTreeType
```

**描述：**

定义UI树采集类型的枚举。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_NATIVE_MODULE_UI_AGENT_TREE_FULL = 0 | 采集完整UI树，包括不可见、透明、离屏及被遮挡的节点。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVE_MODULE_UI_AGENT_TREE_VISIBLE = 1 | 采集经过可见性、裁剪、离屏和遮挡过滤后的可见UI树。<br>**起始版本：** 26.2.0 |

### OH_ArkUI_NativeModule_UIContentChangeEventCategory

```c
enum OH_ArkUI_NativeModule_UIContentChangeEventCategory
```

**描述：**

定义UI内容变化事件类别的枚举。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_NATIVEMODULE_EVENT_CATEGORY_PAGE = 1U << 0 | 页面切换事件，包括Navigation、Router、Swiper和Tabs的切换事件。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVEMODULE_EVENT_CATEGORY_SCROLL = 1U << 1 | 滚动事件。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVEMODULE_EVENT_CATEGORY_OVERLAY = 1U << 2 | 浮层事件，例如模态、菜单或弹窗事件。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVEMODULE_EVENT_CATEGORY_ALL = ~0U | 所有受支持的事件类别。<br>**起始版本：** 26.2.0 |

### OH_ArkUI_NativeModule_UIContentChangeIgnoreType

```c
enum OH_ArkUI_NativeModule_UIContentChangeIgnoreType
```

**描述：**

定义可忽略的UI内容变化事件类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_NATIVEMODULE_CONTENTCHANGE_IGNORE_SCROLLBY = 1U << 0 | 按指定偏移量滚动（scrollBy）的事件。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVEMODULE_CONTENTCHANGE_IGNORE_SCROLLTO = 1U << 1 | 滚动到指定位置（scrollTo）的事件。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVEMODULE_CONTENTCHANGE_IGNORE_TOAST = 1U << 2 | Toast提示事件。<br>**起始版本：** 26.2.0 |

### OH_ArkUI_NativeModule_UIContentChangeEventType

```c
enum OH_ArkUI_NativeModule_UIContentChangeEventType
```

**描述：**

定义ArkUI状态变化事件类型的枚举。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_NATIVEMODULE_EVENT_PAGE_CHANGE_START = 0 | 页面切换开始。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVEMODULE_EVENT_PAGE_CHANGE_END = 1 | 页面切换结束。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVEMODULE_EVENT_SCROLL_START = 2 | 滚动开始。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVEMODULE_EVENT_SCROLL_END = 3 | 滚动交互及其后续的惯性滚动均已结束。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVEMODULE_EVENT_OVERLAY_SHOW = 4 | 浮层显示完成。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVEMODULE_EVENT_OVERLAY_HIDE = 5 | 浮层消失完成。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVEMODULE_EVENT_SWIPER_START = 6 | Swiper切换开始。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVEMODULE_EVENT_SWIPER_END = 7 | Swiper切换完成；如果存在过渡动画，则该动画也已完成。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVEMODULE_EVENT_SWIPER_CANCEL = 8 | Swiper切换中断，并回弹到起始索引。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVEMODULE_EVENT_TABS_START = 9 | Tabs切换开始事件。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVEMODULE_EVENT_TABS_END = 10 | Tabs切换结束事件。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVEMODULE_EVENT_TABS_CANCEL = 11 | Tabs切换开始后被取消，并回弹到切换开始时的索引。<br>**起始版本：** 26.2.0 |


## 函数说明

### OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback()

```c
typedef void (*OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback)(const OH_ArkUI_NativeModule_UIJsonWrapper *json, void *userData)
```

**描述：**

定义接收感知到的交互事件的回调类型。<br> 回调通过借用的[OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md)对象接收事件数据， 不取得该对象的所有权。对象仅在本次回调执行期间有效，回调不得保留或销毁该对象。 事件数据中的所有位置坐标均相对于屏幕（显示器），单位为物理像素（px）。 事件数据顶层始终包含schemaVersion字段。 顶层结构为{ "schemaVersion": 1, "type": "<event type>", ... }。<br> 各事件类型对应的字段见下方列表。 - 点击手势或点击事件：id、point、count、fingers。 - 长按手势：id、point、actualDuration（毫秒）、action（"end"）。 - 拖动手势：id、point、direction、action（"start" \| "end" \| "cancel"）。 - 捏合手势：id、point（由[x, y]组成的数组）、fingers、action（"start" \| "end" \| "cancel"）； 仅在"end"时包含scale字段。 - 旋转手势：id、point（由[x, y]组成的数组）、fingers、action（"start" \| "end" \| "cancel"）； 仅在"end"时包含angle字段，单位为度。 - 滑动手势：id、downPoint（由[x, y]组成的数组）、upPoint（由[x, y]组成的数组）、 direction、speed、actualSpeed。 - 拖拽事件：action（"start" \| "end"）；"start"时包含id、point、hostName、actualDuration； "end"时包含point、dropResult（"success" \| "fail"）、id（目标节点ID，仅在成功时包含）、hostName。 - 触摸事件：action（"down" \| "up"）、fingerId、point；"down"时还包含id（命中节点ID）。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) *json | [in] 借用的JSON对象，仅在本次回调执行期间有效。 |
| void *userData | [in] 注册时传入的自定义用户数据，可以为NULL。框架不取得其所有权， 也不会解引用或释放该指针。 |

### OH_ArkUI_NativeModule_UIInfoCollectionRegisterInteractionObserver()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIInfoCollectionRegisterInteractionObserver(ArkUI_ContextHandle uiContext, uint32_t eventMask, uint32_t *registerID, OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback callback, void *userData)
```

**描述：**

注册UI交互事件观察者。<br> 观察者仅接收eventMask指定类型的事件回调。同一个UI实例可以注册多个观察者。 使用相同的callback和userData组合重复注册，会创建一个新的独立观察者，并分配新的注册ID。<br> 不再使用观察者时，必须调用[OH_ArkUI_NativeModule_UIInfoCollectionUnregisterInteractionObserver](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectionunregisterinteractionobserver) 注销回调。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-contexthandle.md) uiContext | [in] 指向UI实例的指针，不能为NULL。 |
| uint32_t eventMask | [in] 要监听的事件类型位掩码，由 [OH_ArkUI_NativeModule_UIInfoCollection_InteractionEventType](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollection_interactioneventtype)的枚举值按位或组合而成。 支持的标志位范围为OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_TAP至 OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_TOUCH，范围外的位会被忽略。 如果未设置任何受支持的标志位，则返回ARKUI_ERROR_CODE_PARAM_INVALID。 |
| uint32_t *registerID | [out] 用于接收观察者注册ID的指针，不能为NULL。 其指向的值无需初始化；注册成功时写入注册ID，失败时设置为0。 |
| [OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectioninteractionjsoncallback) callback | [in] 匹配事件发生时调用的回调函数，不能为NULL。 |
| void *userData | [in] 传给回调的自定义用户数据，可以为NULL。框架不取得其所有权； 调用方必须保证该数据在观察者注销前一直有效。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR 操作成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID 必填指针参数为NULL，或eventMask未包含任何受支持的标志位。</li> <li>ARKUI_ERROR_CODE_UI_CONTEXT_INVALID UI上下文无效。</li> </ul> |

### OH_ArkUI_NativeModule_UIInfoCollectionUnregisterInteractionObserver()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIInfoCollectionUnregisterInteractionObserver(uint32_t registerID)
```

**描述：**

注销交互事件观察者。<br> 本次调用完成后，不再调用对应的回调函数。<br> 本函数是线程安全的，可以从任意线程调用，且不会阻塞调用方，但不具备异步信号安全性。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint32_t registerID | [in] 注册成功时返回的注册ID。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR 操作成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID 注册ID无效。</li> </ul> |

### OH_ArkUI_NativeModule_UIAgentJsonCallback()

```c
typedef void (*OH_ArkUI_NativeModule_UIAgentJsonCallback)(ArkUI_ContextHandle context, uint64_t requestId, ArkUI_ErrorCode errorCode, OH_ArkUI_NativeModule_UIJsonWrapper *json, void *userData)
```

**描述：**

定义异步JSON树采集请求完成时调用的回调函数类型。<br> 每个被接受的请求均在UI线程上触发且仅触发一次回调。 仅当errorCode为ARKUI_ERROR_CODE_NO_ERROR时，回调才会接收非NULL的JSON对象并取得其所有权。 调用方必须调用OH_ArkUI_NativeModule_UIJsonWrapperDestroy释放该对象。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**资源释放：** ui_json_wrapper/OH_ArkUI_NativeModule_UIJsonWrapperDestroy {json}.

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-contexthandle.md) context | [in] 发起请求时使用的UI上下文。 |
| uint64_t requestId | [in] 分配给已接受请求的标识符。 |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) errorCode | [in] 请求的处理结果。 |
| [OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) *json | [in] 不可变的JSON结果。请求失败时为NULL，成功时包含以JSON结构表示的控件树。 JSON对象顶层包含schemaVersion字段。开发者必须在使用完毕后释放该对象。 |
| void *userData | [in] 调用方传给OH_ArkUI_NativeModule_UIAgentGetTreeJsonAsync的数据。 可以为NULL，表示未提供自定义上下文。 该指针被原样传回，框架不会解引用或释放其指向的数据。 数据的所有权仍归调用方，调用方必须保证数据在本次回调返回前一直有效。 |

### OH_ArkUI_NativeModule_UIAgentTreeRequestCreate()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestCreate(OH_ArkUI_NativeModule_UIAgentTreeType treeType, OH_ArkUI_NativeModule_UIAgentTreeRequest **request)
```

**描述：**

创建UI树采集请求。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**资源释放：** OH_ArkUI_NativeModule_UIAgentTreeRequestDestroy {request}

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeType](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreetype) treeType | [in] UI树类型，必须为OH_ArkUI_NativeModule_UIAgentTreeType中的枚举值。 |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) **request | [out] 用于接收创建的请求对象的输出参数。 调用方必须调用OH_ArkUI_NativeModule_UIAgentTreeRequestDestroy释放该对象。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR 请求创建成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID 输入或输出参数无效。</li> <li>ARKUI_ERROR_CODE_RESOURCE_EXHAUSTED 内存分配失败。</li> </ul> |

### OH_ArkUI_NativeModule_UIAgentTreeRequestDestroy()

```c
void OH_ArkUI_NativeModule_UIAgentTreeRequestDestroy(OH_ArkUI_NativeModule_UIAgentTreeRequest *request)
```

**描述：**

销毁UI树采集请求对象。<br> 传入NULL时不执行任何操作。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [in] 要销毁的请求对象。 |

### OH_ArkUI_NativeModule_UIAgentTreeRequestSetFilterPureLayoutNodes()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetFilterPureLayoutNodes(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)
```

**描述：**

设置是否从返回的UI树中过滤纯布局节点。<br> 默认不启用过滤。启用后，被过滤节点下仍需保留的后代节点会挂载到最近的、仍被保留的祖先节点， 并保持原有的相对顺序。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [in] 要配置的请求对象。 |
| bool enabled | [in] 是否过滤纯布局节点。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR 选项设置成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID request为NULL。</li> </ul> |

### OH_ArkUI_NativeModule_UIAgentTreeRequestSetFilterOccludedNodes()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetFilterOccludedNodes(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)
```

**描述：**

设置是否从返回的UI树中过滤被完全遮挡的节点。<br> 默认不启用过滤，且仅可对可见树采集请求启用此选项。开启遮挡过滤可能给采集带来较大的额外计算量，请根据界面复杂程度酌情使用。 关闭此选项不会关闭可见性过滤、裁剪过滤、离屏节点过滤或完全透明节点过滤。<br> 作为遮挡方的节点所需满足的不透明度阈值由 [OH_ArkUI_NativeModule_UIAgentTreeRequestSetOcclusionOpacityThreshold](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreerequestsetocclusionopacitythreshold)单独配置。 修改此选项不会改变该阈值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [in] 要配置的请求对象，不能为NULL。 |
| bool enabled | [in] true表示启用遮挡过滤，false表示关闭遮挡过滤。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR 选项设置成功。对完整树采集请求设置false也会成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID request为NULL。</li> <li>ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED 对完整树采集请求将enabled设置为true。此时请求对象保持不变。若需启用此选项，请使用可见树采集请求。</li> </ul> |

### OH_ArkUI_NativeModule_UIAgentTreeRequestSetOcclusionOpacityThreshold()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetOcclusionOpacityThreshold(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, float threshold)
```

**描述：**

设置节点作为遮挡方参与遮挡判断时，其最终不透明度必须达到的最小值。<br> 默认值为1.0，仅可见树采集请求支持此选项。 只有满足阈值条件的遮挡节点的区域并集完全覆盖目标节点的有效可见区域时，才会移除目标节点。<br> 如果未通过[OH_ArkUI_NativeModule_UIAgentTreeRequestSetFilterOccludedNodes](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreerequestsetfilteroccludednodes)启用遮挡过滤， 此阈值不会生效。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [in] UI树采集请求。 |
| float threshold | [in] 不透明度阈值，取值范围为[0.0, 1.0]。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR 阈值设置成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID request为NULL。</li> <li>ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGE threshold超出有效范围。</li> <li>ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED 请求为完整树采集请求。</li> </ul> |

### OH_ArkUI_NativeModule_UIAgentTreeRequestSetInteractionInfo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetInteractionInfo(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)
```

**描述：**

设置是否采集额外的交互信息。<br> 默认不启用采集。启用后，结果中会包含受支持的交互信息，例如节点是否可点击、可获焦或可编辑。 此选项不会注册事件观察者，也不会改变任何节点的交互行为。<br> 关闭此选项不会移除默认精简结果中已有的字段。 高级属性采集不会隐式启用此选项，也不会采集此选项专属的字段。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [in] 要配置的请求对象，不能为NULL。 |
| bool enabled | [in] true表示采集交互信息，false表示不采集。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR 选项设置成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID request为NULL。</li> </ul> |

### OH_ArkUI_NativeModule_UIAgentTreeRequestSetAccessibilityInfo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetAccessibilityInfo(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)
```

**描述：**

设置是否采集额外的无障碍信息。<br> 默认不启用采集。启用后，结果中会包含受支持的无障碍信息，例如无障碍内容。 此选项不会启用无障碍服务，也不会改变节点行为。<br> 关闭此选项不会移除默认精简结果中已有的字段。 高级属性采集不会隐式启用此选项，也不会采集此选项专属的字段。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [in] 要配置的请求对象，不能为NULL。 |
| bool enabled | [in] true表示采集无障碍信息，false表示不采集。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR 选项设置成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID request为NULL。</li> </ul> |

### OH_ArkUI_NativeModule_UIAgentTreeRequestSetCollectVisualProperties()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetCollectVisualProperties(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)
```

**描述：**

设置是否采集高级视觉属性。<br> 默认不启用采集。启用后，结果中会额外包含受支持的、用于描述可直接感知的外观的属性， 例如视觉样式和显示状态。<br> 默认精简结果中已有的属性不会重复采集。无论交互信息和无障碍信息采集选项是否启用， 这两类信息的专属字段均不属于本组属性。内部诊断属性始终不会包含在内。<br> 此选项独立于高级功能属性采集选项，不会改变UI树中保留的节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [in] 要配置的请求对象，不能为NULL。 |
| bool enabled | [in] true表示采集高级视觉属性，false表示不采集。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR 选项设置成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID request为NULL。</li> </ul> |

### OH_ArkUI_NativeModule_UIAgentTreeRequestSetCollectFunctionalProperties()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetCollectFunctionalProperties(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)
```

**描述：**

设置是否采集高级功能属性。<br> 默认不启用采集。启用后，结果中会额外包含受支持的属性，用于描述开发者配置的组件行为和功能能力。<br> 默认精简结果中已有的属性不会重复采集。无论交互信息和无障碍信息采集选项是否启用， 这两类信息的专属字段均不属于本组属性。内部诊断属性始终不会包含在内。<br> 此选项独立于高级视觉属性采集选项，不会改变UI树中保留的节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [in] 要配置的请求对象，不能为NULL。 |
| bool enabled | [in] true表示采集高级功能属性，false表示不采集。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR 选项设置成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID request为NULL。</li> </ul> |

### OH_ArkUI_NativeModule_UIAgentGetTreeJson()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentGetTreeJson(ArkUI_ContextHandle context, const OH_ArkUI_NativeModule_UIAgentTreeRequest *request, OH_ArkUI_NativeModule_UIJsonFormat format, OH_ArkUI_NativeModule_UIJsonWrapper **json)
```

**描述：**

同步采集UI树，并以JSON格式返回。<br> 本函数必须在UI线程上调用。结果最多包含5000个节点，大小不得超过5 MiB。 大小限制以规范的紧凑格式JSON为准；如果带缩进和换行的格式化输出本身超过5 MiB，请求同样失败。 不会返回部分JSON数据。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**资源释放：** ui_json_wrapper/OH_ArkUI_NativeModule_UIJsonWrapperDestroy {json}

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-contexthandle.md) context | [in] 待采集UI树所属的UI上下文。 |
| [const OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [in] 采集请求。 |
| [OH_ArkUI_NativeModule_UIJsonFormat](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonformat) format | [in] JSON输出格式。 |
| [OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) **json | [out] 用于接收不可变JSON结果对象的输出参数，不能为NULL， 且必须指向在整个调用期间有效的可写存储空间。调用方无需预先初始化*json。 成功时，*json为非NULL，结果对象顶层包含schemaVersion字段。调用方拥有结果对象的所有权， 必须调用[OH_ArkUI_NativeModule_UIJsonWrapperDestroy](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy)释放该对象。 任何失败时，只要json指向有效的可写存储空间，*json均置为NULL，调用方无需释放结果对象。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR 采集成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID 参数或输出格式无效。</li> <li>ARKUI_ERROR_CODE_UI_CONTEXT_INVALID UI上下文无效。</li> <li>ARKUI_ERROR_CODE_NODE_ON_INVALID_THREAD 在非UI线程上调用。</li> <li>ARKUI_ERROR_CODE_RESULT_TOO_LARGE 结果超出节点数量或大小限制。</li> <li>ARKUI_ERROR_CODE_RESOURCE_EXHAUSTED 内存分配失败。</li> <li>ARKUI_ERROR_CODE_INTERNAL_ERROR 发生其他内部错误。</li> </ul> |

### OH_ArkUI_NativeModule_UIAgentGetTreeJsonAsync()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentGetTreeJsonAsync(ArkUI_ContextHandle context, const OH_ArkUI_NativeModule_UIAgentTreeRequest *request, OH_ArkUI_NativeModule_UIJsonFormat format, OH_ArkUI_NativeModule_UIAgentJsonCallback callback, void *userData, uint64_t *requestId)
```

**描述：**

发起异步UI树采集请求，并通过异步回调接收采集结果。<br> 本函数必须在UI线程上调用。函数返回前会复制request和format， 因此调用方可以在调用返回后立即销毁或复用请求对象。 每个被接受的请求都在UI线程上完成，且仅完成一次。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-contexthandle.md) context | [in] 待采集UI树所属的UI上下文。 |
| [const OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [in] 采集请求。 |
| [OH_ArkUI_NativeModule_UIJsonFormat](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonformat) format | [in] JSON输出格式。 |
| [OH_ArkUI_NativeModule_UIAgentJsonCallback](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagentjsoncallback) callback | [in] 请求完成时调用的回调函数。请求成功时，回调取得JSON对象的所有权， 必须调用OH_ArkUI_NativeModule_UIJsonWrapperDestroy释放该对象。 JSON对象顶层包含schemaVersion字段。 |
| void *userData | [in] 调用方提供的、传给回调的数据，可以为NULL，表示未提供自定义上下文。 框架仅保存指针值直至请求完成，并将其原样传回，不会复制、解引用或释放指针指向的数据。 数据归调用方所有，调用方必须保证数据在完成回调返回前一直有效；请求被同步拒绝时不保留该指针。 |
| uint64_t *requestId | [out] 用于接收已接受请求的标识符的输出参数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR 请求已被接受。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID 参数或输出格式无效。</li> <li>ARKUI_ERROR_CODE_UI_CONTEXT_INVALID UI上下文无效。</li> <li>ARKUI_ERROR_CODE_NODE_ON_INVALID_THREAD 在非UI线程上调用。</li> <li>ARKUI_ERROR_CODE_COMMAND_UNFINISHED 上一次请求尚未完成。</li> </ul> |

### OH_ArkUI_NativeModule_UIAgentGetPageText()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentGetPageText(ArkUI_ContextHandle uiContext, OH_ArkUI_NativeModule_UIJsonWrapper** pageText)
```

**描述：**

同步采集当前ArkUI页面的文本，并以JSON格式输出。<br> 每个JSON项包含用于标识控件的整数"id"、相对于目标窗口的矩形区域"rect"， 以及表示文本内容的字符串"content"。 使用完毕后，必须调用OH_ArkUI_NativeModule_UIJsonWrapperDestroy释放结果所占用的内存。 本函数必须在UI线程上调用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**资源释放：** ui_json_wrapper/OH_ArkUI_NativeModule_UIJsonWrapperDestroy {pageText}

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-contexthandle.md) uiContext | [in] 要采集文本的目标UI实例的上下文。 |
| [OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md)** pageText | [out] 用于接收结果对象的输出参数。调用方应将其指向的对象指针初始化为NULL。 调用成功时，调用方拥有返回对象的所有权，必须在不再使用时调用 [OH_ArkUI_NativeModule_UIJsonWrapperDestroy](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy)释放该对象。 调用失败时，若输出参数有效，则将其指向的对象指针设置为NULL。 调用成功时，返回的JSON对象顶层包含schemaVersion字段，即使页面为空也必须携带该字段。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR 操作成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID pageText为NULL。</li> <li>ARKUI_ERROR_CODE_UI_CONTEXT_INVALID uiContext为NULL或已失效。</li> <li>ARKUI_ERROR_CODE_CAPI_INIT_ERROR Native实现不可用。</li> <li>ARKUI_ERROR_CODE_INTERNAL_ERROR 当前页面不存在、JSON数据的大小无法用uint32_t表示，或采集、序列化失败。</li> </ul> |

### OH_ArkUI_NativeModule_UIContentChangeEventCallback()

```c
typedef void (*OH_ArkUI_NativeModule_UIContentChangeEventCallback)(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, void* userData)
```

**描述：**

定义已注册的ArkUI状态变化事件触发时调用的回调函数类型。<br> 回调在注册时指定的UI上下文所关联的UI线程上执行。 事件快照不可修改，且仅在本次回调返回前有效。 ArkUI仅借用userData，不取得其所有权，也不会访问或释放其指向的数据。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_NativeModule_UIContentChangeEvent](capi-arkui-nativemodule-oh-arkui-nativemodule-uicontentchangeevent.md)* event | [in] 指向不可变事件快照的指针。 |
| void* userData | [in] 注册回调时传入的指针，可以为NULL。 |

### OH_ArkUI_NativeModule_RegisterUIContentChangeEvent()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_RegisterUIContentChangeEvent(ArkUI_ContextHandle uiContext, bool withStart, uint32_t eventMask, uint32_t ignoreMask, void* userData, OH_ArkUI_NativeModule_UIContentChangeEventCallback callback, uint64_t* subscriptionId)
```

**描述：**

为指定UI上下文注册所选类别的ArkUI状态变化事件订阅。<br> 每次成功调用都会创建一个独立订阅。返回的订阅ID非零，且在该UI上下文内唯一。 回调在该UI上下文关联的UI线程上同步执行。 ArkUI仅借用uiContext和userData，不会释放两者。操作失败时，不修改subscriptionId指向的值。 本函数必须在UI线程上调用；从非UI线程调用会导致进程终止。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-contexthandle.md) uiContext | [in] 要监听的UI上下文。该句柄必须在订阅存续期间保持有效。 |
| bool withStart | [in] 是否上报开始事件。true表示上报开始事件，例如页面切换开始、滚动开始； false表示仅上报结束事件。 |
| uint32_t eventMask | [in] 要订阅的事件类别，由 [OH_ArkUI_NativeModule_UIContentChangeEventCategory](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventcategory)的枚举值按位或组合而成，不能为0。 [OH_ARKUI_NATIVEMODULE_EVENT_CATEGORY_SCROLL](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventcategory)类别不区分滚动子类型。 如需忽略特定滚动事件，请在ignoreMask中设置 [OH_ARKUI_NATIVEMODULE_CONTENTCHANGE_IGNORE_SCROLLTO](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeignoretype)或 [OH_ARKUI_NATIVEMODULE_CONTENTCHANGE_IGNORE_SCROLLBY](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeignoretype)对应的标志位。 |
| uint32_t ignoreMask | [in] 要忽略的事件类型，由 [OH_ArkUI_NativeModule_UIContentChangeIgnoreType](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeignoretype)的枚举值按位或组合而成。 |
| void* userData | [in] 传给回调的用户自定义数据。该指针可以为NULL，数据的所有权归调用方。 |
| [OH_ArkUI_NativeModule_UIContentChangeEventCallback](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventcallback) callback | [in] 匹配事件发生时调用的回调函数，不能为NULL。 |
| uint64_t* subscriptionId | [out] 用于接收订阅ID的指针。操作成功时写入非零订阅ID。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR 操作成功。</li> <li>ARKUI_ERROR_CODE_UI_CONTEXT_INVALID uiContext为NULL或不再处于活跃状态。</li> <li>ARKUI_ERROR_CODE_CALLBACK_INVALID callback为NULL。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID eventMask或subscriptionId无效。</li> <li>ARKUI_ERROR_CODE_CAPI_INIT_ERROR Native模块尚未初始化。</li> </ul> |

### OH_ArkUI_NativeModule_UnRegisterUIContentChangeEvent()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UnRegisterUIContentChangeEvent(ArkUI_ContextHandle uiContext, uint64_t subscriptionId)
```

**描述：**

注销指定UI上下文中仍然有效的ArkUI状态变化事件订阅。<br> 本函数成功返回后，后续事件将不再触发已移除订阅的回调，调用方随后可以释放其userData。 在回调中取消订阅，不会改变当前正在分发的这一批回调。 本函数必须在UI线程上调用；从非UI线程调用会导致进程终止。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-contexthandle.md) uiContext | [in] 订阅所属的UI上下文。 |
| uint64_t subscriptionId | [in] 属于uiContext且仍然有效的订阅ID，必须为非零值。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR 操作成功。</li> <li>ARKUI_ERROR_CODE_UI_CONTEXT_INVALID uiContext为NULL或不再处于活跃状态。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID subscriptionId为0、无法识别，或对应订阅已被移除。</li> <li>ARKUI_ERROR_CODE_CAPI_INIT_ERROR Native C接口尚未初始化。</li> </ul> |

### OH_ArkUI_NativeModule_UIContentChangeEventGetType()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIContentChangeEventGetType(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, OH_ArkUI_NativeModule_UIContentChangeEventType* type)
```

**描述：**

从ArkUI状态变化事件快照中获取事件类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_NativeModule_UIContentChangeEvent](capi-arkui-nativemodule-oh-arkui-nativemodule-uicontentchangeevent.md)* event | [in] 指向事件快照的指针，仅在回调执行期间有效。 |
| [OH_ArkUI_NativeModule_UIContentChangeEventType](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventtype)* type | [out] 用于接收事件类型的指针，操作成功时写入。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR 操作成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID event或type为NULL。</li> </ul> |

### OH_ArkUI_NativeModule_UIContentChangeEventGetTimestamp()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIContentChangeEventGetTimestamp(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, uint64_t* nanoTimestamp)
```

**描述：**

获取ArkUI状态变化事件快照的单调时间戳。<br> 该时间戳在事件完成时记录，单位为纳秒，使用单调时钟，不表示日历时间。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_NativeModule_UIContentChangeEvent](capi-arkui-nativemodule-oh-arkui-nativemodule-uicontentchangeevent.md)* event | [in] 指向事件快照的指针，仅在回调执行期间有效。 |
| uint64_t* nanoTimestamp | [out] 用于接收单调时间戳的指针，操作成功时写入，单位为纳秒。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR 操作成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID event或nanoTimestamp为NULL。</li> </ul> |

### OH_ArkUI_NativeModule_UIContentChangeEventGetContext()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIContentChangeEventGetContext(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, ArkUI_ContextHandle* uiContext)
```

**描述：**

获取与ArkUI状态变化事件快照关联的UI上下文。<br> 返回的句柄为借用句柄，调用方不拥有其所有权，不得释放该句柄，也不得在回调返回后使用该句柄。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_NativeModule_UIContentChangeEvent](capi-arkui-nativemodule-oh-arkui-nativemodule-uicontentchangeevent.md)* event | [in] 指向事件快照的指针，仅在回调执行期间有效。 |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-contexthandle.md)* uiContext | [out] 用于接收借用的UI上下文句柄的指针，操作成功时写入。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR 操作成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID event或uiContext为NULL。</li> </ul> |

### OH_ArkUI_NativeModule_UIContentChangeEventGetContentChangeEventJson()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIContentChangeEventGetContentChangeEventJson(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, const OH_ArkUI_NativeModule_UIJsonWrapper** json)
```

**描述：**

从ArkUI状态变化事件快照中获取内容变化事件详情，并以JSON封装对象返回。<br> JSON输出的顶层包含schemaVersion字段，并包含内容变化类型、触发节点、目标节点、浮层类型， 以及根据事件类别决定是否包含的子树转储信息。<br> 页面事件标识目标页面，滚动事件标识发生滚动的节点，浮层事件标识浮层节点并提供浮层类型，例如"dialog"。 触发节点是引起内容变化的节点，在浮层事件和一般的开始、结束场景中可用。 对于页面事件和滚动事件，如果无法提供触发节点，则该节点为NULL。 如果无法提供目标节点，操作仍然成功，返回的JSON中仍包含schemaVersion字段。 JSON封装对象中引用的句柄均为借用句柄，不得释放，也不得在回调返回后使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_NativeModule_UIContentChangeEvent](capi-arkui-nativemodule-oh-arkui-nativemodule-uicontentchangeevent.md)* event | [in] 指向事件快照的指针，仅在回调执行期间有效。 |
| [const OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md)** json | [out] 用于接收包含内容变化事件详情的[OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md)对象的输出参数。 调用方不得释放该封装对象，也不得在回调返回后使用该对象。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR 操作成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID event或json为NULL。</li> </ul> |

### OH_ArkUI_NativeModule_ImageCollectionCallback()

```c
typedef void (*OH_ArkUI_NativeModule_ImageCollectionCallback)(ArkUI_ErrorCode errorCode, OH_ArkUI_NativeModule_ImageCollection* collection, void* userData)
```

**描述：**

定义用于返回ArkUI节点图像采集结果的回调函数类型。<br> 对于每个被接受的请求，框架都会在UI线程上调用且仅调用一次此回调。 当<b>errorCode</b>为ARKUI_ERROR_CODE_NO_ERROR时，框架将非<b>NULL</b>的 <b>collection</b>的所有权转移给调用方。当<b>errorCode</b>为 ARKUI_ERROR_CODE_INTERNAL_ERROR或ARKUI_ERROR_CODE_UI_CONTEXT_INVALID时， <b>collection</b>为<b>NULL</b>。<br> 框架将<b>userData</b>原样传回，不会解引用该指针，也不会复制或释放其指向的对象。 调用方必须保证该对象在回调结束使用前一直有效。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**资源释放：** OH_ArkUI_NativeModule_ImageCollectionDestroy {collection}

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) errorCode | [in] 请求的整体处理结果。 <ul> <li>ARKUI_ERROR_CODE_NO_ERROR 表示采集成功。</li> <li>ARKUI_ERROR_CODE_INTERNAL_ERROR 表示采集过程中发生内部错误。</li> <li>ARKUI_ERROR_CODE_UI_CONTEXT_INVALID 表示请求被接受后，UI上下文失效。</li> </ul> |
| [OH_ArkUI_NativeModule_ImageCollection](capi-arkui-nativemodule-oh-arkui-nativemodule-imagecollection.md)* collection | [in] 结果集合。请求整体成功时为非<b>NULL</b>值，整体失败时为<b>NULL</b>。 |
| void* userData | [in] 调用方自定义的上下文指针，可以为<b>NULL</b>。 |

### OH_ArkUI_NativeModule_GetImagesByNodeIdAsync()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_GetImagesByNodeIdAsync(ArkUI_ContextHandle context, const int32_t* nodeIds, uint32_t count, OH_ArkUI_NativeModule_ImageCollectionCallback callback, void* userData)
```

**描述：**

异步采集指定ArkUI节点ID对应的图像。<br> 单次请求可包含<b>1</b>到<b>20</b>个互不重复的节点ID。 框架会在本函数返回前复制<b>nodeIds</b>数组。 如果<b>count</b>为<b>0</b>或大于<b>20</b>，本函数返回 ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGE。<br> 每个被接受的节点ID在结果集合中都有对应的结果项，即使未找到该节点或无法截取其图像。 对于<b>Image</b>节点，如果可以获取其源<b>PixelMap</b>，则返回完整的源<b>PixelMap</b>； 否则，对节点边界内的渲染内容进行截图。非<b>Image</b>节点同样对节点边界内的渲染内容进行截图。 节点无需处于可见状态。<br> 如果找不到请求的节点ID对应的ArkUI节点，对应结果项会报告 <b>ARKUI_ERROR_CODE_NODE_NOT_FOUND</b>，调用方应检查节点ID。 截图超时时，对应结果项报告<b>ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_TIMEOUT</b>，调用方可以重试请求。 发生其他内部截图错误时，对应结果项报告<b>ARKUI_ERROR_CODE_INTERNAL_ERROR</b>， 调用方可以在处理该错误后重试请求。单个结果项失败不会改变请求整体成功的结果。<br> 调用方可以从任意线程调用本函数。对于每个被接受的请求， 框架都会在<b>context</b>关联的UI线程上调用且仅调用一次<b>callback</b>。 如果上一次请求尚未完成，本函数返回ARKUI_ERROR_CODE_COMMAND_UNFINISHED。 调用方必须等待该请求完成后再提交下一次请求。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-contexthandle.md) context | [in] 用于处理请求的ArkUI上下文，不能为<b>NULL</b>。 |
| const int32_t* nodeIds | [in] 指向节点ID数组首元素的指针。数组包含<b>count</b>个互不重复的ArkUI节点ID， 指针不能为NULL。 |
| uint32_t count | [in] 节点ID的数量，有效范围为(0, 20]。 |
| [OH_ArkUI_NativeModule_ImageCollectionCallback](capi-ui-info-collection-h.md#oh_arkui_nativemodule_imagecollectioncallback) callback | [in] 用于接收结果的回调函数，不能为<b>NULL</b>。 |
| void* userData | [in] 调用方自定义的上下文指针，会原样传给回调，可以为<b>NULL</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR 框架已接受请求。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID context、nodeIds或callback为NULL。</li> <li>ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGE count为0或大于20。</li> <li>ARKUI_ERROR_CODE_COMMAND_UNFINISHED 上一次请求尚未完成。</li> </ul> |

### OH_ArkUI_NativeModule_ImageCollectionTakeItemByNodeId()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImageCollectionTakeItemByNodeId(OH_ArkUI_NativeModule_ImageCollection* collection, int32_t nodeId, OH_PixelmapNative** outPixelmap, ArkUI_ErrorCode* outItemError)
```

**描述：**

取出指定节点ID对应的结果。<br> 对于图像采集成功的结果项，本函数将<b>PixelMap</b>的所有权转移给调用方。 调用方必须调用<b>OH_PixelmapNative_Destroy</b>释放该对象。 本函数也可取出图像采集失败的结果项，此时会将<b>*outPixelmap</b>设置为<b>NULL</b>， 并将该结果项的错误码写入<b>*outItemError</b>。集合中每个节点ID对应的结果仅可取出一次。<br> 销毁集合时，仅释放调用方尚未取出的<b>PixelMap</b>实例， 已转移给调用方的<b>PixelMap</b>不会因此失效。<br> 调用方不得针对同一个集合，将本函数与其他集合操作接口并发调用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**资源释放：** multimedia/image_framework/image/OH_PixelmapNative_Destroy {outPixelmap}

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_NativeModule_ImageCollection](capi-arkui-nativemodule-oh-arkui-nativemodule-imagecollection.md)* collection | [in] 要从中取出结果项的图像集合，不能为NULL。 |
| int32_t nodeId | [in] 要取出的结果项对应的ArkUI节点ID。 |
| [OH_PixelmapNative](../../apis-image-kit/c-apis/capi-image-nativemodule-oh-pixelmapnative.md)** outPixelmap | [out] 用于接收所有权已转移的PixelMap的输出参数，不能为NULL。 对于失败的结果项，其指向的PixelMap指针会被设置为NULL。 |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode)* outItemError | [out] 用于接收该结果项错误码的输出参数，不能为NULL。 采集成功时写入ARKUI_ERROR_CODE_NO_ERROR； 采集图像时未找到请求的节点ID对应的ArkUI节点，写入ARKUI_ERROR_CODE_NODE_NOT_FOUND； 截图超时时写入ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_TIMEOUT； 发生其他截图错误时写入ARKUI_ERROR_CODE_INTERNAL_ERROR，调用方可以重试请求。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR 成功取出结果项，包括图像采集失败的结果项。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID 必填指针参数为NULL、nodeId在collection中没有对应的结果项，或该结果项已被取出。请提供所有必填指针参数，并确保nodeId对应collection中尚未取出的结果项。</li> </ul> |

### OH_ArkUI_NativeModule_ImageCollectionDestroy()

```c
void OH_ArkUI_NativeModule_ImageCollectionDestroy(OH_ArkUI_NativeModule_ImageCollection* collection)
```

**描述：**

销毁图像集合，并释放尚未取出的<b>PixelMap</b>实例。<br> 调用方必须销毁回调返回的每个非<b>NULL</b>集合，即使其中的所有结果项均已取出。 本函数不会释放通过<b>OH_ArkUI_NativeModule_ImageCollectionTakeItemByNodeId</b> 取得的<b>PixelMap</b>实例，也不会使这些实例失效。<br> 调用方不得针对同一个集合，将本函数与其他集合操作接口并发调用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_NativeModule_ImageCollection](capi-arkui-nativemodule-oh-arkui-nativemodule-imagecollection.md)* collection | [in] 要销毁的图像集合，可以为<b>NULL</b>。 如果<b>collection</b>为<b>NULL</b>，则不执行任何操作。 |


