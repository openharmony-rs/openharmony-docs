# native_node.h

## 概述

提供NativeNode接口的类型定义。

**引用文件：** <arkui/native_node.h>

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述                                                                           |
| -- | -- |------------------------------------------------------------------------------|
| [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) | ArkUI_AttributeItem | 定义[setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setAttribute)函数通用入参结构。 |
| [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) | ArkUI_NodeComponentEvent | 定义组件回调事件的参数类型。                                                               |
| [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) | ArkUI_StringAsyncEvent | 定义组件回调事件使用字符串参数的类型。                                                          |
| [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md) | ArkUI_TextChangeEvent | 定义组件事件的混合类型数据。                                                               |
| [ArkUI_NativeNodeAPI_1](capi-arkui-nativemodule-arkui-nativenodeapi-1.md) | ArkUI_NativeNodeAPI_1 | ArkUI提供的Native侧Node类型接口集合。Node模块相关接口需要在主线程上调用。                               |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) | ArkUI_NodeEvent | 定义组件事件的通用结构类型。                                                               |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md) | ArkUI_NodeCustomEvent | 定义自定义组件事件的通用结构类型。                                                            |
| [ArkUI_NodeAdapter*](capi-arkui-nativemodule-arkui-nodeadapter8h.md) | ArkUI_NodeAdapterHandle | 定义组件适配器对象，用于滚动类组件的元素懒加载。                                                     |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md) | ArkUI_NodeAdapterEvent | 定义适配器事件对象。                                                                   |
| [ArkUI_NodeContentEvent](capi-arkui-nativemodule-arkui-nodecontentevent.md) | ArkUI_NodeContentEvent | 定义NodeContent事件的通用结构类型。                                                      |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_NodeType](#arkui_nodetype) | ArkUI_NodeType | 提供ArkUI在Native侧可创建组件类型。 |
| [ArkUI_NodeAttributeType](#arkui_nodeattributetype) | ArkUI_NodeAttributeType | 定义ArkUI在Native侧可以设置的属性样式集合。 |
| [ArkUI_NodeEventType](#arkui_nodeeventtype) | ArkUI_NodeEventType | 提供NativeNode组件支持的事件类型定义。 |
| [ArkUI_NodeDirtyFlag](#arkui_nodedirtyflag) | ArkUI_NodeDirtyFlag | 自定义组件调用<b>::markDirty</b>是传递的脏区标识类型。 |
| [ArkUI_NodeCustomEventType](#arkui_nodecustomeventtype) | ArkUI_NodeCustomEventType | 定义自定义组件事件类型。 |
| [ArkUI_NodeAdapterEventType](#arkui_nodeadaptereventtype) | ArkUI_NodeAdapterEventType | 定义节点适配器事件枚举值。 |
| [ArkUI_NodeContentEventType](#arkui_nodecontenteventtype) | ArkUI_NodeContentEventType | 定义NodeContent事件类型。 |
| [ArkUI_InspectorErrorCode](#arkui_inspectorerrorcode) | ArkUI_InspectorErrorCode | inspector错误码的枚举。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_NodeEventType OH_ArkUI_NodeEvent_GetEventType(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_geteventtype) | - | 获取组件事件类型。 |
| [int32_t OH_ArkUI_NodeEvent_GetTargetId(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_gettargetid) | - | 获取事件自定义标识ID。该事件id在调用[registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent)函数时作为参数传递进来，可应用于同一事件入口函数[registerNodeEventReceiver](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeeventreceiver)分发逻辑。 |
| [ArkUI_NodeHandle OH_ArkUI_NodeEvent_GetNodeHandle(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getnodehandle) | - | 获取触发该事件的组件对象。 |
| [ArkUI_UIInputEvent* OH_ArkUI_NodeEvent_GetInputEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getinputevent) | - | 获取组件事件中的输入事件（如触碰事件）数据。 |
| [ArkUI_NodeComponentEvent* OH_ArkUI_NodeEvent_GetNodeComponentEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getnodecomponentevent) | - | 获取组件事件中的数字类型数据。 |
| [ArkUI_StringAsyncEvent* OH_ArkUI_NodeEvent_GetStringAsyncEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getstringasyncevent) | - | 获取组件事件中的字符串数据。 |
| [ArkUI_TextChangeEvent* OH_ArkUI_NodeEvent_GetTextChangeEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_gettextchangeevent) | - | 获取组件事件中的ArkUI_TextChangeEvent数据。 |
| [void* OH_ArkUI_NodeEvent_GetUserData(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getuserdata) | - | 获取组件事件中的用户自定义数据。该自定义参数在调用[registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent)函数时作为参数传递进来，可应用于事件触发时的业务逻辑处理。 |
| [int32_t OH_ArkUI_NodeEvent_GetNumberValue(ArkUI_NodeEvent* event, int32_t index, ArkUI_NumberValue* value)](#oh_arkui_nodeevent_getnumbervalue) | - | 获取组件回调事件的数字类型参数。 |
| [int32_t OH_ArkUI_NodeEvent_GetStringValue(ArkUI_NodeEvent* event, int32_t index, char** string, int32_t* stringSize)](#oh_arkui_nodeevent_getstringvalue) | - | 获取组件回调事件的字符串类型参数，字符串数据仅在事件回调过程中有效，需要在事件回调外使用建议进行额外拷贝处理。 |
| [int32_t OH_ArkUI_NodeEvent_SetReturnNumberValue(ArkUI_NodeEvent* event, ArkUI_NumberValue* value, int32_t size)](#oh_arkui_nodeevent_setreturnnumbervalue) | - | 设置组件回调事件的返回值。 |
| [ArkUI_NodeAdapterHandle OH_ArkUI_NodeAdapter_Create()](#oh_arkui_nodeadapter_create) | - | 创建组件适配器对象。 |
| [void OH_ArkUI_NodeAdapter_Dispose(ArkUI_NodeAdapterHandle handle)](#oh_arkui_nodeadapter_dispose) | - | 销毁组件适配器对象。 |
| [int32_t OH_ArkUI_NodeAdapter_SetTotalNodeCount(ArkUI_NodeAdapterHandle handle, uint32_t size)](#oh_arkui_nodeadapter_settotalnodecount) | - | 设置Adapter中的元素总数。 |
| [uint32_t OH_ArkUI_NodeAdapter_GetTotalNodeCount(ArkUI_NodeAdapterHandle handle)](#oh_arkui_nodeadapter_gettotalnodecount) | - | 获取Adapter中的元素总数。 |
| [int32_t OH_ArkUI_NodeAdapter_RegisterEventReceiver(ArkUI_NodeAdapterHandle handle, void* userData, void (\*receiver)(ArkUI_NodeAdapterEvent* event))](#oh_arkui_nodeadapter_registereventreceiver) | - | 注册Adapter相关回调事件。 |
| [void OH_ArkUI_NodeAdapter_UnregisterEventReceiver(ArkUI_NodeAdapterHandle handle)](#oh_arkui_nodeadapter_unregistereventreceiver) | - | 注销Adapter相关回调事件。 |
| [int32_t OH_ArkUI_NodeAdapter_ReloadAllItems(ArkUI_NodeAdapterHandle handle)](#oh_arkui_nodeadapter_reloadallitems) | - | 通知Adapter进行全量元素变化。 |
| [int32_t OH_ArkUI_NodeAdapter_ReloadItem(ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)](#oh_arkui_nodeadapter_reloaditem) | - | 通知Adapter进行局部元素变化。 |
| [int32_t OH_ArkUI_NodeAdapter_RemoveItem(ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)](#oh_arkui_nodeadapter_removeitem) | - | 通知Adapter进行局部元素删除。 |
| [int32_t OH_ArkUI_NodeAdapter_InsertItem(ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)](#oh_arkui_nodeadapter_insertitem) | - | 通知Adapter进行局部元素插入。 |
| [int32_t OH_ArkUI_NodeAdapter_MoveItem(ArkUI_NodeAdapterHandle handle, uint32_t from, uint32_t to)](#oh_arkui_nodeadapter_moveitem) | - | 通知Adapter进行局部元素移位。 |
| [int32_t OH_ArkUI_NodeAdapter_GetAllItems(ArkUI_NodeAdapterHandle handle, ArkUI_NodeHandle** items, uint32_t* size)](#oh_arkui_nodeadapter_getallitems) | - | 获取存储在Adapter中的所有元素。接口调用会返回元素的数组对象指针，该指针指向的内存数据需要开发者手动释放。 |
| [void* OH_ArkUI_NodeAdapterEvent_GetUserData(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_getuserdata) | - | 获取注册事件时传入的自定义数据。 |
| [ArkUI_NodeAdapterEventType OH_ArkUI_NodeAdapterEvent_GetType(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_gettype) | - | 获取事件类型。 |
| [ArkUI_NodeHandle OH_ArkUI_NodeAdapterEvent_GetRemovedNode(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_getremovednode) | - | 获取需要销毁的事件中待销毁的元素。 |
| [uint32_t OH_ArkUI_NodeAdapterEvent_GetItemIndex(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_getitemindex) | - | 获取适配器事件时需要操作的元素序号。 |
| [ArkUI_NodeHandle OH_ArkUI_NodeAdapterEvent_GetHostNode(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_gethostnode) | - | 获取使用该适配器的滚动类容器节点。 |
| [int32_t OH_ArkUI_NodeAdapterEvent_SetItem(ArkUI_NodeAdapterEvent* event, ArkUI_NodeHandle node)](#oh_arkui_nodeadapterevent_setitem) | - | 设置需要新增到Adapter中的组件。 |
| [int32_t OH_ArkUI_NodeAdapterEvent_SetNodeId(ArkUI_NodeAdapterEvent* event, int32_t id)](#oh_arkui_nodeadapterevent_setnodeid) | - | 设置生成的组件标识。 |
| [ArkUI_LayoutConstraint* OH_ArkUI_NodeCustomEvent_GetLayoutConstraintInMeasure(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_getlayoutconstraintinmeasure) | - | 通过自定义组件事件获取测算过程中的约束尺寸。 |
| [ArkUI_IntOffset OH_ArkUI_NodeCustomEvent_GetPositionInLayout(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_getpositioninlayout) | - | 通过自定义组件事件获取在布局阶段期望自身相对父组件的位置。 |
| [ArkUI_DrawContext* OH_ArkUI_NodeCustomEvent_GetDrawContextInDraw(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_getdrawcontextindraw) | - | 通过自定义组件事件获取绘制上下文。 |
| [int32_t OH_ArkUI_NodeCustomEvent_GetEventTargetId(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_geteventtargetid) | - | 通过自定义组件事件获取自定义事件ID。 |
| [void* OH_ArkUI_NodeCustomEvent_GetUserData(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_getuserdata) | - | 通过自定义组件事件获取自定义事件参数。 |
| [ArkUI_NodeHandle OH_ArkUI_NodeCustomEvent_GetNodeHandle(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_getnodehandle) | - | 通过自定义组件事件获取组件对象。 |
| [ArkUI_NodeCustomEventType OH_ArkUI_NodeCustomEvent_GetEventType(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_geteventtype) | - | 通过自定义组件事件获取事件类型。 |
| [int32_t OH_ArkUI_NodeCustomEvent_GetCustomSpanMeasureInfo(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanMeasureInfo* info)](#oh_arkui_nodecustomevent_getcustomspanmeasureinfo) | - | 通过自定义组件事件获取自定义段落组件的测量信息。 |
| [int32_t OH_ArkUI_NodeCustomEvent_SetCustomSpanMetrics(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanMetrics* metrics)](#oh_arkui_nodecustomevent_setcustomspanmetrics) | - | 通过自定义组件事件设置自定义段落的度量指标。 |
| [int32_t OH_ArkUI_NodeCustomEvent_GetCustomSpanDrawInfo(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_nodecustomevent_getcustomspandrawinfo) | - | 通过自定义组件事件获取自定义段落组件的绘制信息。 |
| [typedef void (\*ArkUI_NodeContentCallback)(ArkUI_NodeContentEvent* event)](#arkui_nodecontentcallback) | ArkUI_NodeContentCallback | 定义NodeContent事件的回调函数类型。 |
| [int32_t OH_ArkUI_NodeContent_RegisterCallback(ArkUI_NodeContentHandle content, ArkUI_NodeContentCallback callback)](#oh_arkui_nodecontent_registercallback) | - | 注册NodeContent事件函数。 |
| [ArkUI_NodeContentEventType OH_ArkUI_NodeContentEvent_GetEventType(ArkUI_NodeContentEvent* event)](#oh_arkui_nodecontentevent_geteventtype) | - | 获取触发NodeContent事件的事件类型。 |
| [ArkUI_NodeContentHandle OH_ArkUI_NodeContentEvent_GetNodeContentHandle(ArkUI_NodeContentEvent* event)](#oh_arkui_nodecontentevent_getnodecontenthandle) | - | 获取触发事件的NodeContent对象。 |
| [int32_t OH_ArkUI_NodeContent_SetUserData(ArkUI_NodeContentHandle content, void* userData)](#oh_arkui_nodecontent_setuserdata) | - | 在NodeContent对象上保存自定义数据。 |
| [void* OH_ArkUI_NodeContent_GetUserData(ArkUI_NodeContentHandle content)](#oh_arkui_nodecontent_getuserdata) | - | 获取在NodeContent对象上保存的自定义数据。 |
| [int32_t OH_ArkUI_NodeContent_AddNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node)](#oh_arkui_nodecontent_addnode) | - | 将一个ArkUI组件节点添加到对应的NodeContent对象下。 |
| [int32_t OH_ArkUI_NodeContent_RemoveNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node)](#oh_arkui_nodecontent_removenode) | - | 删除NodeContent对象下的一个ArkUI组件节点。 |
| [int32_t OH_ArkUI_NodeContent_InsertNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node, int32_t position)](#oh_arkui_nodecontent_insertnode) | - | 将一个ArkUI组件节点插入到对应的NodeContent对象的特定位置下。 |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutSize(ArkUI_NodeHandle node, ArkUI_IntSize* size)](#oh_arkui_nodeutils_getlayoutsize) | - | 获取组件布局区域的大小。布局区域大小不包含图形变化属性，如缩放。 |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutPosition(ArkUI_NodeHandle node, ArkUI_IntOffset* localOffset)](#oh_arkui_nodeutils_getlayoutposition) | - | 获取组件布局区域相对父组件的位置。布局区域相对位置不包含图形变化属性，如平移。 |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInWindow(ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset)](#oh_arkui_nodeutils_getlayoutpositioninwindow) | - | 获取组件布局区域相对窗口的位置。布局区域相对位置不包含图形变化属性，如平移。 |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInScreen(ArkUI_NodeHandle node, ArkUI_IntOffset* screenOffset)](#oh_arkui_nodeutils_getlayoutpositioninscreen) | - | 获取组件布局区域相对屏幕的位置。布局区域相对位置不包含图形变化属性，如平移。 |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInGlobalDisplay(ArkUI_NodeHandle node, ArkUI_IntOffset* offset)](#oh_arkui_nodeutils_getlayoutpositioninglobaldisplay) | - | 获取组件相对于全局屏幕的偏移。布局区域相对位置不包含图形变化属性，如平移。 |
| [int32_t OH_ArkUI_NodeUtils_GetPositionWithTranslateInWindow(ArkUI_NodeHandle node, ArkUI_IntOffset* translateOffset)](#oh_arkui_nodeutils_getpositionwithtranslateinwindow) | - | 获取组件在窗口中的位置，包含了图形平移变化属性。 |
| [int32_t OH_ArkUI_NodeUtils_GetPositionWithTranslateInScreen(ArkUI_NodeHandle node, ArkUI_IntOffset* translateOffset)](#oh_arkui_nodeutils_getpositionwithtranslateinscreen) | - | 获取组件在屏幕中的位置，包含了图形平移变化属性。 |
| [void OH_ArkUI_NodeUtils_AddCustomProperty(ArkUI_NodeHandle node, const char* name, const char* value)](#oh_arkui_nodeutils_addcustomproperty) | - | 设置组件的自定义属性。该接口仅在主线程生效。 |
| [void OH_ArkUI_NodeUtils_RemoveCustomProperty(ArkUI_NodeHandle node, const char* name)](#oh_arkui_nodeutils_removecustomproperty) | - | 移除组件已设置的自定义属性。 |
| [int32_t OH_ArkUI_NodeUtils_GetCustomProperty(ArkUI_NodeHandle node, const char* name, ArkUI_CustomProperty** handle)](#oh_arkui_nodeutils_getcustomproperty) | - | 获取组件的自定义属性的值。 |
| [ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetParentInPageTree(ArkUI_NodeHandle node)](#oh_arkui_nodeutils_getparentinpagetree) | - | 获取父节点，可获取由ArkTs创建的组件节点。 |
| [int32_t OH_ArkUI_NodeUtils_GetActiveChildrenInfo(ArkUI_NodeHandle head, ArkUI_ActiveChildrenInfo** handle)](#oh_arkui_nodeutils_getactivechildreninfo) | - | 获取某个节点所有活跃的子节点。Span将不会被计入子结点的统计中。 |
| [ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetCurrentPageRootNode(ArkUI_NodeHandle node)](#oh_arkui_nodeutils_getcurrentpagerootnode) | - | 获取当前页面的根节点。 |
| [bool OH_ArkUI_NodeUtils_IsCreatedByNDK(ArkUI_NodeHandle node)](#oh_arkui_nodeutils_iscreatedbyndk) | - | 获取组件是否由C-API创建的标签。 |
| [int32_t OH_ArkUI_NodeUtils_GetNodeType(ArkUI_NodeHandle node)](#oh_arkui_nodeutils_getnodetype) | - | 获取节点的类型。 |
| [int32_t OH_ArkUI_NodeUtils_GetWindowInfo(ArkUI_NodeHandle node, ArkUI_HostWindowInfo** info)](#oh_arkui_nodeutils_getwindowinfo) | - | 获取节点所属的窗口信息。 |
| [int32_t OH_ArkUI_NodeUtils_MoveTo(ArkUI_NodeHandle node, ArkUI_NodeHandle target_parent, int32_t index)](#oh_arkui_nodeutils_moveto) | - | 将节点移动到目标父节点下，作为子节点。 |
| [int32_t OH_ArkUI_List_CloseAllSwipeActions(ArkUI_NodeHandle node, void* userData, void (\*onFinish)(void* userData))](#oh_arkui_list_closeallswipeactions) | - | 收起展开状态下的ListItem。 |
| [ArkUI_ContextHandle OH_ArkUI_GetContextByNode(ArkUI_NodeHandle node)](#oh_arkui_getcontextbynode) | - | 获取当前节点所在页面的UI的上下文实例对象指针。 |
| [int32_t OH_ArkUI_RegisterSystemColorModeChangeEvent(ArkUI_NodeHandle node,void* userData, void (\*onColorModeChange)(ArkUI_SystemColorMode colorMode, void* userData))](#oh_arkui_registersystemcolormodechangeevent) | - | 注册系统深浅色变更事件。同一组件仅能注册一个系统深浅变更回调。示例请参考：[监听组件事件](../../ui/ndk-listen-to-component-events.md)。 |
| [void OH_ArkUI_UnregisterSystemColorModeChangeEvent(ArkUI_NodeHandle node)](#oh_arkui_unregistersystemcolormodechangeevent) | - | 注销系统深浅色变更事件。 |
| [int32_t OH_ArkUI_RegisterSystemFontStyleChangeEvent(ArkUI_NodeHandle node,void* userData, void (\*onFontStyleChange)(ArkUI_SystemFontStyleEvent* event, void* userData))](#oh_arkui_registersystemfontstylechangeevent) | - | 注册系统字体变更事件。同一组件仅能注册一个系统字体变更回调。 |
| [void OH_ArkUI_UnregisterSystemFontStyleChangeEvent(ArkUI_NodeHandle node)](#oh_arkui_unregistersystemfontstylechangeevent) | - | 注销系统字体变更事件。 |
| [float OH_ArkUI_SystemFontStyleEvent_GetFontSizeScale(const ArkUI_SystemFontStyleEvent* event)](#oh_arkui_systemfontstyleevent_getfontsizescale) | - | 获取系统字体变更事件的字体大小值。 |
| [float OH_ArkUI_SystemFontStyleEvent_GetFontWeightScale(const ArkUI_SystemFontStyleEvent* event)](#oh_arkui_systemfontstyleevent_getfontweightscale) | - | 获取系统字体变更事件的字体粗细值。 |
| [int32_t OH_ArkUI_RegisterLayoutCallbackOnNodeHandle(ArkUI_NodeHandle node,void* userData, void (\*onLayoutCompleted)(void* userData))](#oh_arkui_registerlayoutcallbackonnodehandle) | - | 注册指定节点的布局完成回调函数。 |
| [int32_t OH_ArkUI_RegisterDrawCallbackOnNodeHandle(ArkUI_NodeHandle node,void* userData, void (\*onDrawCompleted)(void* userData))](#oh_arkui_registerdrawcallbackonnodehandle) | - | 注册指定节点的绘制完成回调函数。 |
| [int32_t OH_ArkUI_UnregisterLayoutCallbackOnNodeHandle(ArkUI_NodeHandle node)](#oh_arkui_unregisterlayoutcallbackonnodehandle) | - | 取消注册指定节点的布局完成回调函数。 |
| [int32_t OH_ArkUI_UnregisterDrawCallbackOnNodeHandle(ArkUI_NodeHandle node)](#oh_arkui_unregisterdrawcallbackonnodehandle) | - | 取消注册指定节点的绘制完成回调函数。 |
| [int32_t OH_ArkUI_GetNodeSnapshot(ArkUI_NodeHandle node, ArkUI_SnapshotOptions* snapshotOptions,OH_PixelmapNative** pixelmap)](#oh_arkui_getnodesnapshot) | - | 获取给定组件的截图，若节点不在组件树上或尚未渲染，截图操作将会失败。当pixelmap不再使用时，应通过调用OH_PixelmapNative_Release来释放。 |
| [int32_t OH_ArkUI_NodeUtils_GetAttachedNodeHandleById(const char* id, ArkUI_NodeHandle* node)](#oh_arkui_nodeutils_getattachednodehandlebyid) | - | 根据用户id获取目标节点。 |
| [int32_t OH_ArkUI_NodeUtils_GetNodeHandleByUniqueId(const uint32_t uniqueId, ArkUI_NodeHandle* node)](#oh_arkui_nodeutils_getnodehandlebyuniqueid) | - | 通过uniqueId获取节点。 |
| [int32_t OH_ArkUI_NodeUtils_GetNodeUniqueId(ArkUI_NodeHandle node, int32_t* uniqueId)](#oh_arkui_nodeutils_getnodeuniqueid) | - | 获取目标节点的uniqueId。 |
| [int32_t OH_ArkUI_NodeUtils_SetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)](#oh_arkui_nodeutils_setcrosslanguageoption) | - | 设置目标节点跨语言设置属性的能力。 |
| [int32_t OH_ArkUI_NodeUtils_GetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)](#oh_arkui_nodeutils_getcrosslanguageoption) | - | 获取目标节点跨语言设置属性的配置项。 |
| [int32_t OH_ArkUI_NodeUtils_GetFirstChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)](#oh_arkui_nodeutils_getfirstchildindexwithoutexpand) | - | 获取目标节点在树上的第一个子节点的下标。 |
| [int32_t OH_ArkUI_NodeUtils_GetLastChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)](#oh_arkui_nodeutils_getlastchildindexwithoutexpand) | - | 获取目标节点在树上的最后一个子节点的下标。 |
| [int32_t OH_ArkUI_NodeUtils_GetChildWithExpandMode(ArkUI_NodeHandle node, int32_t position,ArkUI_NodeHandle* subnode, uint32_t expandMode)](#oh_arkui_nodeutils_getchildwithexpandmode) | - | 用不同的展开模式获取对应下标的子节点。 |
| [int32_t OH_ArkUI_NodeUtils_GetPositionToParent(ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset)](#oh_arkui_nodeutils_getpositiontoparent) | - | 获取目标节点相对于父节点的偏移值，单位：px。 |
| [ArkUI_ErrorCode OH_ArkUI_AddSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates,void (statesChangeHandler)(int32_t currentStates, void* userData), bool excludeInner, void* userData)](#oh_arkui_addsupporteduistates) | - | 设置组件支持的多态样式状态。为了更高效地处理，需传入所关注的状态值及对应的状态处理函数，当关注的状态发生时，处理函数会被执行。可在回调中根据当前状态调整UI样式。当在同一个节点上多次调用该方法时，将以最后一次传入的状态及处理函数为准。有些类型的组件节点，系统内部已有对某些状态的默认处理。例如，Button组件默认具备对PRESSED状态的样式变化，当在此类组件上使用此方法自定义状态处理时，会先应用系统默认样式变化，再执行自定义的样式处理，最终效果为两者叠加。可以通过指定excludeInner为true来禁用系统内部的默认样式效果，但这通常取决于系统内部实现规范是否允许。当调用该函数时，传入的statesChangeHandler函数会立即执行一次，且无需特意注册对NORMAL状态的监听，只要注册了非NORMAL状态，当状态从任意状态变化回NORMAL时，系统都会进行回调，以便应用进行样式复原。 |
| [ArkUI_ErrorCode OH_ArkUI_RemoveSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates)](#oh_arkui_removesupporteduistates) | - | 删除注册的状态处理。当通过OH_ArkUI_AddSupportedUIStates注册的状态都被删除时，所注册的stateChangeHandler也不会再被执行。 |
| [int32_t OH_ArkUI_RunTaskInScope(ArkUI_ContextHandle uiContext, void* userData, void(\*callback)(void* userData))](#oh_arkui_runtaskinscope) | - | 在目标UI上下文中执行传入的自定义回调函数。示例请参考：[在NDK中保证多实例场景功能正常](../../ui/ndk-scope-task.md)。 |

## 枚举类型说明

### ArkUI_NodeType

```
enum ArkUI_NodeType
```

**描述：**


提供ArkUI在Native侧可创建组件类型。

**起始版本：** 12

| 枚举项 | 描述                                   |
| -- |--------------------------------------|
| ARKUI_NODE_CUSTOM = 0 | 自定义节点。                               |
| ARKUI_NODE_TEXT = 1 | 文本。                                  |
| ARKUI_NODE_SPAN = 2 | 文本段落。                                |
| ARKUI_NODE_IMAGE_SPAN = 3 | 文本图片段落。                              |
| ARKUI_NODE_IMAGE = 4 | 图片。                                  |
| ARKUI_NODE_TOGGLE = 5 | 状态开关。                                |
| ARKUI_NODE_LOADING_PROGRESS = 6 | 等待图标。                                |
| ARKUI_NODE_TEXT_INPUT = 7 | 单行文本输入。                              |
| ARKUI_NODE_TEXT_AREA = 8 | 多行文本。                                |
| ARKUI_NODE_BUTTON = 9 | 按钮。                                  |
| ARKUI_NODE_PROGRESS = 10 | 进度条。                                 |
| ARKUI_NODE_CHECKBOX = 11 | 复选框。                                 |
| ARKUI_NODE_XCOMPONENT = 12 | SURFACE类型XComponent。                 |
| ARKUI_NODE_DATE_PICKER = 13 | 日期选择器组件。                             |
| ARKUI_NODE_TIME_PICKER = 14 | 时间选择组件。                              |
| ARKUI_NODE_TEXT_PICKER = 15 | 滑动选择文本内容的组件。                         |
| ARKUI_NODE_CALENDAR_PICKER = 16 | 日历选择器组件。                             |
| ARKUI_NODE_SLIDER = 17 | 滑动条组件。                               |
| ARKUI_NODE_RADIO = 18 | 单选框。                                 |
| ARKUI_NODE_IMAGE_ANIMATOR = 19 | 帧动画组件。                               |
| ARKUI_NODE_XCOMPONENT_TEXTURE | TEXTURE类型XComponent。<br>**起始版本：** 16 |
| ARKUI_NODE_CHECKBOX_GROUP = 21 | 复选框组。<br>**起始版本：** 15                |
| ARKUI_NODE_STACK = MAX_NODE_SCOPE_NUM | 堆叠容器。                                |
| ARKUI_NODE_SWIPER | 翻页容器。                                |
| ARKUI_NODE_SCROLL | 滚动容器。                                |
| ARKUI_NODE_LIST | 列表。                                  |
| ARKUI_NODE_LIST_ITEM | 列表项。                                 |
| ARKUI_NODE_LIST_ITEM_GROUP | 列表item分组。                            |
| ARKUI_NODE_COLUMN | 垂直布局容器。                              |
| ARKUI_NODE_ROW | 水平布局容器。                              |
| ARKUI_NODE_FLEX | 弹性布局容器。                              |
| ARKUI_NODE_REFRESH | 刷新组件。                                |
| ARKUI_NODE_WATER_FLOW | 瀑布流容器。                               |
| ARKUI_NODE_FLOW_ITEM | 瀑布流子组件。                              |
| ARKUI_NODE_RELATIVE_CONTAINER | 相对布局组件。                              |
| ARKUI_NODE_GRID | 网格容器。                                |
| ARKUI_NODE_GRID_ITEM | 网格子组件。                               |
| ARKUI_NODE_CUSTOM_SPAN | 自定义文本段落。                             |
| ARKUI_NODE_EMBEDDED_COMPONENT |                                      |

### ArkUI_NodeAttributeType

```
enum ArkUI_NodeAttributeType
```

**描述：**


定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

| 枚举项 |描述                                                                                 |
| -- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| NODE_WIDTH = 0 | 宽度属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：宽度数值，单位为vp；<br>属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：宽度数值，单位为vp；|
| NODE_HEIGHT | 高度属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：高度数值，单位为vp；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：高度数值，单位为vp；|
| NODE_BACKGROUND_COLOR | 背景色属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：背景色数值，0xargb格式，形如 0xFFFF0000 表示红色；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：背景色数值，0xargb格式，形如 0xFFFF0000 表示红色；|
| NODE_BACKGROUND_IMAGE | 背景色图片属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string: 图片地址，支持网络图片地址、本地图片地址、Base64或PixelMap对象。不支持SVG类型的图片。<br> .value[0]?.i32：可选值，repeat参数，参数类型[ArkUI_ImageRepeat](capi-native-type-h.md#arkui_imagerepeat)，默认值为ARKUI_IMAGE_REPEAT_NONE；<br> .object：PixelMap 图片数据，参数类型为[ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string: 图片地址，支持网络图片地址、本地图片地址、Base64或PixelMap对象。不支持SVG类型的图片。<br> .value[0].i32：repeat参数，参数类型[ArkUI_ImageRepeat](capi-native-type-h.md#arkui_imagerepeat)；<br> .object：PixelMap 图片数据， 参数类型为[ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)；.object参数和.string参数二选一，不可同时设置。|
| NODE_PADDING | 内间距属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：<br> 1：上下左右四个位置的内间距值相等。<br> .value[0].f32：内间距数值，单位为vp；<br> 2：分别指定上下左右四个位置的内间距值。<br> .value[0].f32：上内间距数值，单位为vp；<br> .value[1].f32：右内间距数值，单位为vp；<br> .value[2].f32：下内间距数值，单位为vp；<br> .value[3].f32：左内间距数值，单位为vp；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：上内间距数值，单位为vp；<br> .value[1].f32：右内间距数值，单位为vp；<br> .value[2].f32：下内间距数值，单位为vp；<br> .value[3].f32：左内间距数值，单位为vp；|
| NODE_ID | 组件ID属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string: ID的内容；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string: ID的内容；|
| NODE_ENABLED | 设置组件是否可交互，支持属性设置，属性重置和属性获取。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：false表示不可交互，true表示可交互；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：0表示不可交互，1表示可交互；|
| NODE_MARGIN | 外间距属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：<br> 1：上下左右四个位置的外间距值相等。<br> .value[0].f32：外间距数值，单位为vp；<br> 2：分别指定上下左右四个位置的外间距值。<br> .value[0].f32：上外间距数值，单位为vp；<br> .value[1].f32：右外间距数值，单位为vp；<br> .value[2].f32：下外间距数值，单位为vp；<br> .value[3].f32：左外间距数值，单位为vp；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：上外间距数值，单位为vp；<br> .value[1].f32：右外间距数值，单位为vp；<br> .value[2].f32：下外间距数值，单位为vp；<br> .value[3].f32：左外间距数值，单位为vp；|
| NODE_TRANSLATE | 设置组件平移，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32： x轴移动距离，单位vp，默认值0；<br> .value[1].f32： y轴移动距离，单位vp，默认值0；<br> .value[2].f32： z轴移动距离，单位vp，默认值0。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32： x轴移动距离，单位vp；<br> .value[1].f32： y轴移动距离，单位vp；<br> .value[2].f32： z轴移动距离，单位vp。|
| NODE_SCALE | 设置组件缩放，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32： x轴的缩放系数，默认值1；<br> .value[1].f32： y轴的缩放系数，默认值1。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32： x轴的缩放系数；<br> .value[1].f32： y轴的缩放系数。|
| NODE_ROTATE | 设置组件旋转，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32： 旋转轴向量x坐标，默认值0；<br> .value[1].f32： 旋转轴向量y坐标，默认值0；<br> .value[2].f32： 旋转轴向量z坐标，默认值0；<br> .value[3].f32： 旋转角度，默认值0；<br> .value[4].f32： 视距，即视点到z=0平面的距离，单位vp，默认值0。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32： 旋转轴向量x坐标；<br> .value[1].f32： 旋转轴向量y坐标；<br> .value[2].f32： 旋转轴向量z坐标；<br> .value[3].f32： 旋转角度；<br> .value[4].f32： 视距，即视点到z=0平面的距离，单位vp。|
| NODE_BRIGHTNESS | 设置组件高光效果，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32： 亮度值，默认值1.0，推荐取值范围[0,2]。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32： 亮度值。|
| NODE_SATURATION | 设置组件饱和度效果，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32： 饱和度值，默认值1.0，推荐取值范围[0,50)。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32： 饱和度值。 |
| NODE_BLUR | 设置组件内容模糊效果，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32： 模糊半径，模糊半径越大越模糊，为0时不模糊，小于0时按0处理且不会返回错误码。单位px，默认值0.0。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32： 模糊半径，模糊半径越大越模糊，为0时不模糊。单位px。|
| NODE_LINEAR_GRADIENT | 设置组件颜色渐变效果，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32： 线性渐变的起始角度，当[ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection)为ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM时，angle属性生效，否则按direction为主要布局方式。0点方向顺时针旋转为正向角度，默认值：180； <br> .value[1].i32：线性渐变的方向，设置除ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM的线性渐变方向后，angle不生效。数据类型[ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection)。 <br> .value[2].i32： 为渐变的颜色重复着色，默认值 false。 <br> .object: 参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过： <br> colors：渐变色颜色颜色。 <br> stops：渐变位置。 <br> size：颜色个数。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32： 线性渐变的起始角度。当为ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM时，angle为设置值，其他情况均为默认值。<br> .value[1].i32：线性渐变的方向。<br> .value[2].i32： 为渐变的颜色重复着色。<br> .object: 参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过： <br> colors：渐变色颜色颜色。 <br> stops：渐变位置。 <br> size：颜色个数。|
| NODE_ALIGNMENT | 设置组件内容在元素绘制区域内的对齐方式，支持属性设置，属性重置和属性获取接口。在Stack中该属性与NODE_STACK_ALIGN_CONTENT效果一致，只能设置子组件在容器内的对齐方式。<br> <br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 对齐方式，数据类型[ArkUI_Alignment](capi-native-type-h.md#arkui_alignment)，默认值ARKUI_ALIGNMENT_CENTER。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 对齐方式，数据类型[ArkUI_Alignment](capi-native-type-h.md#arkui_alignment)。|
| NODE_OPACITY | 透明度属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：透明度数值，取值范围为0到1。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：透明度数值，取值范围为0到1。 |
| NODE_BORDER_WIDTH | 边框宽度属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> 1: .value[0].f32：统一设置四条边的边框宽度。 <br> 2: .value[0].f32：设置上边框的边框宽度。 <br> .value[1].f32：设置右边框的边框宽度。 <br> .value[2].f32：设置下边框的边框宽度。 <br> .value[3].f32：设置左边框的边框宽度。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：设置上边框的边框宽度。 <br> .value[1].f32：设置右边框的边框宽度。 <br> .value[2].f32：设置下边框的边框宽度。 <br> .value[3].f32：设置左边框的边框宽度。|
| NODE_BORDER_RADIUS | 边框圆角属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> 1: .value[0].f32：统一设置四条边的边框圆角。 <br> 2: .value[0].f32：设置左上角圆角半径。 <br> .value[1].f32：设置右上角圆角半径。 <br> .value[2].f32：设置左下角圆角半径。 <br> .value[3].f32：设置右下角圆角半径。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：设置左上角圆角半径。 <br> .value[1].f32：设置右上角圆角半径。 <br> .value[2].f32：设置左下角圆角半径。 <br> .value[3].f32：设置右下角圆角半径。 |
| NODE_BORDER_COLOR | 边框颜色属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> 1: .value[0].u32：统一设置四条边的边框颜色，使用0xargb表示，如0xFFFF11FF。 <br> 2: .value[0].u32：设置上侧边框颜色，使用0xargb表示，如0xFFFF11FF。 <br> .value[1].u32：设置右侧边框颜色，使用0xargb表示，如0xFFFF11FF。 <br> .value[2].u32：设置下侧边框颜色，使用0xargb表示，如0xFFFF11FF。 <br> .value[3].u32：设置左侧边框颜色，使用0xargb表示，如0xFFFF11FF。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].u32：设置上侧边框颜色，使用0xargb表示，如0xFFFF11FF。 <br> .value[1].u32：设置右侧边框颜色，使用0xargb表示，如0xFFFF11FF。 <br> .value[2].u32：设置下侧边框颜色，使用0xargb表示，如0xFFFF11FF。 <br> .value[3].u32：设置左侧边框颜色，使用0xargb表示，如0xFFFF11FF。|
| NODE_BORDER_STYLE | 边框线条样式属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> 1: .value[0].i32：统一设置四条边的边框线条样式，参数类型[ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle)，默认值为ARKUI_BORDER_STYLE_SOLID。 <br> 2:.value[0].i32：设置上侧边框线条样式，参数类型[ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle)，默认值为ARKUI_BORDER_STYLE_SOLID。 <br> .value[1].i32：设置右侧边框线条样式，参数类型[ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle)，默认值为ARKUI_BORDER_STYLE_SOLID。 <br> .value[2].i32：设置下侧边框线条样式，参数类型[ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle)，默认值为ARKUI_BORDER_STYLE_SOLID。 <br> .value[3].i32：设置左侧边框线条样式，参数类型[ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle)，默认值为ARKUI_BORDER_STYLE_SOLID。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：上侧边框线条样式对应的数值。 <br> .value[1].i32：右侧边框线条样式对应的数值。 <br> .value[2].i32：下侧边框线条样式对应的数值。 <br> .value[3].i32：左侧边框线条样式对应的数值。 |
| NODE_Z_INDEX | 组件的堆叠顺序属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：堆叠顺序数值。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：堆叠顺序数值。 |
| NODE_VISIBILITY | 组件是否可见属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：控制当前组件显示或隐藏，参数类型[ArkUI_Visibility](capi-native-type-h.md#arkui_visibility)，默认值为ARKUI_VISIBILITY_VISIBLE。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：控制当前组件显示或隐藏，参数类型[ArkUI_Visibility](capi-native-type-h.md#arkui_visibility)，默认值为ARKUI_VISIBILITY_VISIBLE。|
| NODE_CLIP | 组件进行裁剪、遮罩处理属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：控制是否按照父容器边缘轮廓进行裁剪，0表示不裁切，1表示裁切。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：控制是否按照父容器边缘轮廓进行裁剪，0表示不裁切，1表示裁切。|
| NODE_CLIP_SHAPE | 组件上指定形状的裁剪，支持属性设置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式,共有5种类型： <br> 1.rect类型： <br> .value[0].i32：裁剪类型，参数类型[ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype)，ARKUI_CLIP_TYPE_RECTANGLE； <br> .value[1].f32：矩形宽度； <br> .value[2].f32：矩形高度； <br> .value[3].f32：矩形圆角宽度； <br> .value[4].f32：矩形圆角高度； <br> .value[5]?.f32：矩形形状的左上圆角半径； <br> .value[6]?.f32：矩形形状的左下圆角半径； <br> .value[7]?.f32：矩形形状的右上圆角半径； <br> .value[8]?.f32：矩形形状的右下圆角半径； <br> 2.circle类型： <br> .value[0].i32：裁剪类型，参数类型[ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype)，ARKUI_CLIP_TYPE_CIRCLE； <br> .value[1].f32：圆形宽度； <br> .value[2].f32：圆形高度； <br> 3.ellipse类型： <br> .value[0].i32：裁剪类型，参数类型[ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype)，ARKUI_CLIP_TYPE_ELLIPSE； <br> .value[1].f32：椭圆形宽度； <br> .value[2].f32：椭圆形高度； <br> 4.path类型： <br> .value[0].i32：裁剪类型，参数类型[ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype)，ARKUI_CLIP_TYPE_PATH； <br> .value[1].f32：路径宽度； <br> .value[2].f32：路径高度； <br> .string：路径绘制的命令字符串； <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式,共有5种类型： <br> 1.rect类型： <br> .value[0].i32：裁剪类型，参数类型[ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype)，ARKUI_CLIP_TYPE_RECTANGLE； <br> .value[1].f32：矩形宽度； <br> .value[2].f32：矩形高度； <br> .value[3].f32：矩形圆角宽度； <br> .value[4].f32：矩形圆角高度； <br> .value[5]?.f32：矩形形状的左上圆角半径； <br> .value[6]?.f32：矩形形状的左下圆角半径； <br> .value[7]?.f32：矩形形状的右上圆角半径； <br> .value[8]?.f32：矩形形状的右下圆角半径； <br> 2.circle类型： <br> .value[0].i32：裁剪类型，参数类型[ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype)，ARKUI_CLIP_TYPE_CIRCLE； <br> .value[1].f32：圆形宽度； <br> .value[2].f32：圆形高度； <br> 3.ellipse类型： <br> .value[0].i32：裁剪类型，参数类型[ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype)，ARKUI_CLIP_TYPE_ELLIPSE； <br> .value[1].f32：椭圆形宽度； <br> .value[2].f32：椭圆形高度； <br> 4.path类型： <br> .value[0].i32：裁剪类型，参数类型[ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype)，ARKUI_CLIP_TYPE_PATH； <br> .value[1].f32：路径宽度； <br> .value[2].f32：路径高度； <br> .string：路径绘制的命令字符串； |
| NODE_TRANSFORM | 矩阵变换功能，可对图形进行平移、旋转和缩放等，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0...15].f32: 16个浮点数字。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0...15].f32: 16个浮点数字。|
| NODE_HIT_TEST_BEHAVIOR | 触摸测试类型，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：控制当前组件的触摸测试类型，参数类型[ArkUI_HitTestMode](capi-native-type-h.md#arkui_hittestmode)，默认值为ARKUI_HIT_TEST_MODE_DEFAULT。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：控制当前组件的触摸测试类型，参数类型ArkKUI_HitTestMode，默认值为ARKUI_HIT_TEST_MODE_DEFAULT。 |
| NODE_POSITION | 元素左上角相对于父容器左上角偏移位置，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：x轴坐标。 <br> .value[1].f32: y轴坐标。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：x轴坐标。 <br> .value[1].f32: y轴坐标。 |
| NODE_SHADOW | 阴影效果属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：设置当前组件阴影效果，参数类型[ArkUI_ShadowStyle](capi-native-type-h.md#arkui_shadowstyle)。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：设置当前组件阴影效果，参数类型[ArkUI_ShadowStyle](capi-native-type-h.md#arkui_shadowstyle)。 |
| NODE_CUSTOM_SHADOW | 自定义阴影效果，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0]?.f32：阴影模糊半径，单位为vp；<br> .value[1]?.i32：是否开启智能取色，0代表不开启，1代表开启，默认不开启；<br> .value[2]?.f32：阴影X轴偏移量，单位为px；<br> .value[3]?.f32：阴影Y轴偏移量，单位为px；<br> .value[4]?.i32：阴影类型[ArkUI_ShadowType](capi-native-type-h.md#arkui_shadowtype)，默认值为ARKUI_SHADOW_TYPE_COLOR；<br> .value[5]?.u32：阴影颜色，0xargb格式，形如 0xFFFF0000 表示红色；<br> .value[6]?.u32：阴影是否内部填充，0表示不填充，1表示填充。<br>     <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：阴影模糊半径，单位为vp；<br> .value[1].i32：是否开启智能取色；<br> .value[2].f32：阴影X轴偏移量，单位为px；<br> .value[3].f32：阴影Y轴偏移量，单位为px；<br> .value[4].i32：阴影类型[ArkUI_ShadowType](capi-native-type-h.md#arkui_shadowtype)，默认值为ARKUI_SHADOW_TYPE_COLOR；<br> .value[5].u32：阴影颜色，0xargb格式，形如 0xFFFF0000 表示红色；<br> .value[6].u32：阴影是否内部填充，0表示不填充，1表示填充；|
| NODE_BACKGROUND_IMAGE_SIZE | 背景图片的宽高属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32 表示图片的宽度值，取值范围[0,+∞)，单位为vp。<br> .value[1].f32 表示图片的高度值，取值范围[0,+∞)，单位为vp。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32 表示图片的宽度值，单位为vp。<br> .value[1].f32 表示图片的高度值，单位为vp。 |
| NODE_BACKGROUND_IMAGE_SIZE_WITH_STYLE | 背景图片的宽高样式属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32 表示背景图片的宽高样式，取[ArkUI_ImageSize](capi-native-type-h.md#arkui_imagesize)枚举值。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32 表示背景图片的宽高样式，取[ArkUI_ImageSize](capi-native-type-h.md#arkui_imagesize)枚举值。|
| NODE_BACKGROUND_BLUR_STYLE | 背景和内容之间的模糊属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32 表示模糊类型，取[ArkUI_BlurStyle](capi-native-type-h.md#arkui_blurstyle)枚举值。<br> .value[1]?.i32 表示深浅色模式，取[ArkUI_ColorMode](capi-native-type-h.md#arkui_colormode)枚举值。<br> .value[2]?.i32 表示取色模式，取[ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor)枚举值。<br> .value[3]?.f32 表示模糊效果程度，取[0.0,1.0]范围内的值。<br> .value[4]?.f32 表示灰阶模糊起始边界。<br> .value[5]?.f32 表示灰阶模糊终点边界。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32 表示模糊类型，取[ArkUI_BlurStyle](capi-native-type-h.md#arkui_blurstyle)枚举值。<br> .value[1].i32 表示深浅色模式，取[ArkUI_ColorMode](capi-native-type-h.md#arkui_colormode)枚举值。<br> .value[2].i32 表示取色模式，取[ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor)枚举值。<br> .value[3].f32 表示模糊效果程度，取[0.0,1.0]范围内的值。<br> .value[4].f32 表示灰阶模糊起始边界。<br> .value[5].f32 表示灰阶模糊终点边界。|
| NODE_TRANSFORM_CENTER | 图形变换和转场的中心点属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0]?.f32 表示中心点X轴坐标值，单位为vp。 <br> .value[1]?.f32 表示中心点Y轴坐标，单位为vp。 <br> .value[2]?.f32 表示中心点Z轴坐标，单位为vp。 <br> .value[3]?.f32 表示中心点X轴坐标的百分比位置，如0.2表示百分之20的位置，该属性覆盖value[0].f32，默认值:0.5f。<br> .value[4]?.f32 表示中心点Y轴坐标的百分比位置，如0.2表示百分之20的位置，该属性覆盖value[1].f32，默认值:0.5f。<br> .value[5]?.f32 表示中心点Z轴坐标的百分比位置，如0.2表示百分之20的位置，该属性覆盖value[2].f32，默认值:0.0f。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32 表示中心点X轴坐标，单位为vp。 <br> .value[1].f32 表示中心点Y轴坐标，单位为vp。 <br> .value[2].f32 表示中心点Z轴坐标，单位为vp。 <br> 注：如果设置坐标百分比位置，属性获取方法返回计算后的vp为单位的值。|
| NODE_OPACITY_TRANSITION | 转场时的透明度效果属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32 表示起终点的透明度值。 <br> .value[1].i32 表示动画时长，单位ms。 <br> .value[2].i32 表示动画曲线类型，取[ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve)枚举值。 <br> .value[3]?.i32 表示动画延迟时长，单位ms。 <br> .value[4]?.i32 表示动画播放次数。 <br> .value[5]?.i32 表示动画播放模式，取[ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode)枚举值。 <br> .value[6]?.f32 表示动画播放速度。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32 表示起终点的透明度值。 <br> .value[1].i32 表示动画时长，单位ms。 <br> .value[2].i32 表示动画曲线类型，取[ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve)枚举值。 <br> .value[3].i32 表示动画延迟时长，单位ms。 <br> .value[4].i32 表示动画播放次数。 <br> .value[5].i32 表示动画播放模式，取[ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode)枚举值。 <br> .value[6].f32 表示动画播放速度。 |
| NODE_ROTATE_TRANSITION | 转场时的旋转效果属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32 表示横向旋转分量。<br> .value[1].f32 表示纵向的旋转分量。<br> .value[2].f32 表示竖向的旋转分量。<br> .value[3].f32 表示角度。<br> .value[4].f32 表示视距，默认值：0.0f。<br> .value[5].i32 表示动画时长，单位ms。<br> .value[6].i32 表示动画曲线类型，取[ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve)枚举值。<br> .value[7]?.i32 表示动画延迟时长，单位ms。<br> .value[8]?.i32 表示动画播放次数。<br> .value[9]?.i32 表示动画播放模式，取[ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode)枚举值。<br> .value[10]?.f32 表示动画播放速度。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32 表示横向旋转分量。<br> .value[1].f32 表示纵向的旋转分量。<br> .value[2].f32 表示竖向的旋转分量。<br> .value[3].f32 表示角度。<br> .value[4].f32 表示视距。<br> .value[5].i32 表示动画时长，单位ms。<br> .value[6].i32 表示动画曲线类型，取[ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve)枚举值。<br> .value[7].i32 表示动画延迟时长，单位ms。<br> .value[8].i32 表示动画播放次数。<br> .value[9].i32 表示动画播放模式，取[ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode)枚举值。<br> .value[10].f32 表示动画播放速度。 |
| NODE_SCALE_TRANSITION | 转场时的缩放效果属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32 横向放大倍数。<br> .value[1].f32 纵向放大倍数。<br> .value[2].f32 竖向放大倍数。<br> .value[3].i32 表示动画时长，单位ms。<br> .value[4].i32 表示动画曲线类型，取[ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve)枚举值。<br> .value[5]?.i32 表示动画延迟时长，单位ms。<br> .value[6]?.i32 表示动画播放次数。<br> .value[7]?.i32 表示动画播放模式，取[ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode)枚举值。<br> .value[8]?.f32 表示动画播放速度。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32 横向放大倍数。<br> .value[1].f32 纵向放大倍数。<br> .value[2].f32 竖向放大倍数。<br> .value[3].i32 表示动画时长，单位ms。<br> .value[4].i32 表示动画曲线类型，取[ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve)枚举值。<br> .value[5].i32 表示动画延迟时长，单位ms。<br> .value[6].i32 表示动画播放次数。<br> .value[7].i32 表示动画播放模式，取[ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode)枚举值。<br> .value[8].f32 表示动画播放速度。|
| NODE_TRANSLATE_TRANSITION | 转场时的平移效果属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> value[0].f32 表示横向平移距离值，单位为vp。 <br> value[1].f32 表示纵向平移距离值，单位为vp。 <br> value[2].f32 表示竖向平移距离值，单位为vp。 <br> value[3].i32 表示动画时长，单位ms。<br> value[4].i32 表示动画曲线类型，取[ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve)枚举值。<br> value[5]?.i32 表示动画延迟时长，单位ms。<br> value[6]?.i32 表示动画播放次数。<br> value[7]?.i32 表示动画播放模式，取[ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode)枚举值。<br> value[8]?.f32 表示动画播放速度。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> value[0].f32 表示横向平移距离值，单位为vp。 <br> value[1].f32 表示纵向平移距离值，单位为vp。 <br> value[2].f32 表示竖向平移距离值，单位为vp。 <br> value[3].i32 表示动画时长，单位ms。<br> value[4].i32 表示动画曲线类型，取[ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve)枚举值。<br> value[5].i32 表示动画延迟时长，单位ms。<br> value[6].i32 表示动画播放次数。<br> value[7].i32 表示动画播放模式，取[ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode)枚举值。<br> value[8].f32 表示动画播放速度。|
| NODE_MOVE_TRANSITION | 转场时从屏幕边缘滑入和滑出的效果属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32 参数类型[ArkUI_TransitionEdge](capi-native-type-h.md#arkui_transitionedge)。 <br> .value[1].i32 表示动画时长，单位ms。 <br> .value[2].i32 表示动画曲线类型，取[ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve)枚举值。 <br> .value[3]?.i32 表示动画延迟时长，单位ms。 <br> .value[4]?.i32 表示动画播放次数。 <br> .value[5]?.i32 表示动画播放模式，取[ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode)枚举值。 <br> .value[6]?.f32 表示动画播放速度。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32 参数类型[ArkUI_TransitionEdge](capi-native-type-h.md#arkui_transitionedge)。 <br> .value[1].i32 表示动画时长，单位ms。 <br> .value[2].i32 表示动画曲线类型，取[ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve)枚举值。 <br> .value[3].i32 表示动画延迟时长，单位ms。 <br> .value[4].i32 表示动画播放次数。 <br> .value[5].i32 表示动画播放模式，取[ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode)枚举值。 <br> .value[6].f32 表示动画播放速度。 |
| NODE_FOCUSABLE | 获焦属性，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].i32：参数类型为1或者0。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：参数类型为1或者0。 |
| NODE_DEFAULT_FOCUS | 默认焦点属性，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> value[0].i32：参数类型为1或者0。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> value[0].i32：参数类型为1或者0。 |
| NODE_RESPONSE_REGION | 触摸热区属性，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .data[0].f32：触摸点相对于组件左上角的x轴坐标,单位为vp。 <br> .data[1].f32：触摸点相对于组件左上角的y轴坐标,单位为vp。 <br> .data[2].f32：触摸热区的宽度 ，单位为百分比。 <br> .data[3].f32：触摸热区的高度，单位为百分比。 <br> .data[4...].f32:可以设置多个手势响应区域，顺序和上述一致。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .data[0].f32：触摸点相对于组件左上角的x轴坐标,单位为vp。 <br> .data[1].f32：触摸点相对于组件左上角的y轴坐标,单位为vp。 <br> .data[2].f32：触摸热区的宽度，单位为百分比。 <br> .data[3].f32：触摸热区的高度，单位为百分比。 <br> .data[4...].f32:可以设置多个手势响应区域，顺序和上述一致。  |
| NODE_OVERLAY | 遮罩文本属性，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .string 遮罩文本；<br> .value[0]?.i32：可选值，浮层相对于组件的位置，参数类型[ArkUI_Alignment](capi-native-type-h.md#arkui_alignment)，默认值为ARKUI_ALIGNMENT_TOP_START。 <br> .value[1]?.f32：可选值，浮层基于自身左上角的偏移量X，单位为vp。 <br> .value[2]?.f32：可选值，浮层基于自身左上角的偏移量Y，单位为vp。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .string 遮罩文本； <br> .value[0].i32：浮层相对于组件的位置，参数类型[ArkUI_Alignment](capi-native-type-h.md#arkui_alignment)，默认值为ARKUI_ALIGNMENT_TOP_START。 <br> .value[1].f32：浮层基于自身左上角的偏移量X，单位为vp。 <br> .value[2].f32：浮层基于自身左上角的偏移量Y，单位为vp。 |
| NODE_SWEEP_GRADIENT | 角度渐变效果，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0]?.f32:为角度渐变的中心点，即相对于当前组件左上角的坐标,X轴坐标。 <br> .value[1]?.f32:为角度渐变的中心点，即相对于当前组件左上角的坐标,Y轴坐标。 <br> .value[2]?.f32:角度渐变的起点，默认值0。 <br> .value[3]?.f32:角度渐变的终点，默认值0。 <br> .value[4]?.f32:角度渐变的旋转角度，默认值0。 <br> .value[5]?.i32:为渐变的颜色重复着色，0表示不重复着色，1表示重复着色。 <br> .object: 参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过： <br> colors：渐变色颜色颜色。 <br> stops：渐变位置。 <br> size：颜色个数。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32:为角度渐变的中心点，即相对于当前组件左上角的坐标,X轴坐标。 <br> .value[1].f32:为角度渐变的中心点，即相对于当前组件左上角的坐标,Y轴坐标。 <br> .value[2].f32:角度渐变的起点，默认值0。 <br> .value[3].f32:角度渐变的终点，默认值0。 <br> .value[4].f32:角度渐变的旋转角度，默认值0。 <br> .value[5].i32:为渐变的颜色重复着色，0表示不重复着色，1表示重复着色。 <br> .object: 参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过： <br> colors：渐变色颜色颜色。 <br> stops：渐变位置。 <br> size：颜色个数。|
| NODE_RADIAL_GRADIENT | 径向渐变渐变效果，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0]?.f32:为径向渐变的中心点，即相对于当前组件左上角的坐标,X轴坐标。 <br> .value[1]?.f32:为径向渐变的中心点，即相对于当前组件左上角的坐标,Y轴坐标。 <br> .value[2]?.f32:径向渐变的半径，默认值0。 <br> .value[3]?.i32:为渐变的颜色重复着色，0表示不重复着色，1表示重复着色。 <br> .object: 参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过： <br> colors：渐变色颜色颜色。 <br> stops：渐变位置。 <br> size：颜色个数。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32:为径向渐变的中心点，即相对于当前组件左上角的坐标,X轴坐标。 <br> .value[1].f32:为径向渐变的中心点，即相对于当前组件左上角的坐标,Y轴坐标。 <br> .value[2].f32:径向渐变的半径，默认值0。 <br> .value[3].i32:为渐变的颜色重复着色，0表示不重复着色，1表示重复着色。 <br> .object: 参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过： <br> colors：渐变色颜色颜色。 <br> stops：渐变位置。 <br> size：颜色个数。|
| NODE_MASK | 组件上加上指定形状的遮罩，支持属性设置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式,共有5种类型： <br> 1.rect类型： <br> .value[0].u32：填充颜色，0xargb类型； <br> .value[1].u32：描边颜色，0xargb类型； <br> .value[2].f32：描边宽度，单位为vp； <br> .value[3].i32：遮罩类型，参数类型[ArkUI_MaskType](capi-native-type-h.md#arkui_masktype)，ARKUI_MASK_TYPE_RECTANGLE； <br> .value[4].f32：矩形宽度； <br> .value[5].f32：矩形高度； <br> .value[6].f32：矩形圆角宽度； <br> .value[7].f32：矩形圆角高度； <br> .value[8]?.f32：矩形形状的左上圆角半径； <br> .value[9]?.f32：矩形形状的左下圆角半径； <br> .value[10]?.f32：矩形形状的右上圆角半径； <br> .value[11]?.f32：矩形形状的右下圆角半径； <br> 2.circle类型： <br> .value[0].u32：填充颜色，0xargb类型； <br> .value[1].u32：描边颜色，0xargb类型； <br> .value[2].f32：描边宽度，单位为vp； <br> .value[3].i32：遮罩类型，参数类型[ArkUI_MaskType](capi-native-type-h.md#arkui_masktype)，ARKUI_MASK_TYPE_CIRCLE； <br> .value[4].f32：圆形宽度； <br> .value[5].f32：圆形高度； <br> 3.ellipse类型： <br> .value[0].u32：填充颜色，0xargb类型； <br> .value[1].u32：描边颜色，0xargb类型； <br> .value[2].f32：描边宽度，单位为vp； <br> .value[3].i32：遮罩类型，参数类型[ArkUI_MaskType](capi-native-type-h.md#arkui_masktype)，ARKUI_MASK_TYPE_ELLIPSE； <br> .value[4].f32：椭圆形宽度； <br> .value[5].f32：椭圆形高度； <br> 4.path类型： <br> .value[0].u32：填充颜色，0xargb类型； <br> .value[1].u32：描边颜色，0xargb类型； <br> .value[2].f32：描边宽度，单位为vp； <br> .value[3].i32：遮罩类型，参数类型[ArkUI_MaskType](capi-native-type-h.md#arkui_masktype)，ARKUI_MASK_TYPE_PATH； <br> .value[4].f32：路径宽度； <br> .value[5].f32：路径高度； <br> .string：路径绘制的命令字符串； <br> 5.progress类型： <br> .value[0].i32：遮罩类型，参数类型[ArkUI_MaskType](capi-native-type-h.md#arkui_masktype)，ARKUI_MASK_TYPE_PROGRESS； <br> .value[1].f32：进度遮罩的当前值； <br> .value[2].f32：进度遮罩的最大值； <br> .value[3].u32：进度遮罩的颜色； <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式,共有5种类型： <br> 1.rect类型： <br> .value[0].u32：填充颜色，0xargb类型； <br> .value[1].u32：描边颜色，0xargb类型； <br> .value[2].f32：描边宽度，单位为vp； <br> .value[3].i32：遮罩类型； <br> .value[4].f32：矩形宽度； <br> .value[5].f32：矩形高度； <br> .value[6].f32：矩形圆角宽度； <br> .value[7].f32：矩形圆角高度； <br> .value[8]?.f32：矩形形状的左上圆角半径； <br> .value[9]?.f32：矩形形状的左下圆角半径； <br> .value[10]?.f32：矩形形状的右上圆角半径； <br> .value[11]?.f32：矩形形状的右下圆角半径； <br> 2.circle类型： <br> .value[0].u32：填充颜色，0xargb类型； <br> .value[1].u32：描边颜色，0xargb类型； <br> .value[2].f32：描边宽度，单位为vp； <br> .value[3].i32：遮罩类型； <br> .value[4].f32：圆形宽度； <br> .value[5].f32：圆形高度； <br> 3.ellipse类型： <br> .value[0].u32：填充颜色，0xargb类型； <br> .value[1].u32：描边颜色，0xargb类型； <br> .value[2].f32：描边宽度，单位为vp； <br> .value[3].i32：遮罩类型； <br> .value[4].f32：椭圆形宽度； <br> .value[5].f32：椭圆形高度； <br> 4.path类型： <br> .value[0].u32：填充颜色，0xargb类型； <br> .value[1].u32：描边颜色，0xargb类型； <br> .value[2].f32：描边宽度，单位为vp； <br> .value[3].i32：遮罩类型； <br> .value[4].f32：路径宽度； <br> .value[5].f32：路径高度； <br> .string：路径绘制的命令字符串； <br> 5.progress类型： <br> .value[0].i32：遮罩类型； <br> .value[1].f32：进度遮罩的当前值； <br> .value[2].f32：进度遮罩的最大值； <br> .value[3].u32：进度遮罩的颜色； <br> |
| NODE_BLEND_MODE | 当前控件背景与子节点内容进行混合，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：控制当前组件的混合模式类型，参数类型[ArkUI_BlendMode](capi-native-type-h.md#arkui_blendmode)，默认值为ARKUI_BLEND_MODE_NONE。 <br> .value[1].?i32：blendMode实现方式是否离屏，参数类型[ArkUI_BlendApplyType](capi-native-type-h.md#arkui_blendapplytype)，默认值为BLEND_APPLY_TYPE_FAST。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：控制当前组件的混合模式类型，参数类型[ArkUI_BlendMode](capi-native-type-h.md#arkui_blendmode)，默认值为ARKUI_BLEND_MODE_NONE。 <br> .value[1].i32：blendMode实现方式是否离屏，参数类型[ArkUI_BlendApplyType](capi-native-type-h.md#arkui_blendapplytype)，默认值为BLEND_APPLY_TYPE_FAST。|
| NODE_DIRECTION | 设置容器元素内主轴方向上的布局，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：设置容器元素内主轴方向上的布局类型， <br> 参数类型[ArkUI_Direction](capi-native-type-h.md#arkui_direction)，默认值为ARKUI_DIRECTION_AUTO。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：设置容器元素内主轴方向上的布局类型， <br> 参数类型[ArkUI_Direction](capi-native-type-h.md#arkui_direction)，默认值为ARKUI_DIRECTION_AUTO。|
| NODE_CONSTRAINT_SIZE | 约束尺寸属性，组件布局时，进行尺寸范围限制，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：最小宽度，单位vp； <br> .value[1].f32：最大宽度，单位vp； <br> .value[2].f32：最小高度，单位vp； <br> .value[3].f32：最大高度，单位vp； <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：最小宽度，单位vp； <br> .value[1].f32：最大宽度，单位vp； <br> .value[2].f32：最小高度，单位vp； <br> .value[3].f32：最大高度，单位vp；|
| NODE_GRAY_SCALE | 灰度效果属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：灰度转换比例，范围0-1之间，比如0.5指按照50%进行灰度处理； <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：灰度转换比例，范围0-1之间；|
| NODE_INVERT | 反转输入的图像比例属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：图像反转比例，范围0-1之间，比如0.5指按照50%进行反转处理； <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：图像反转比例，范围0-1之间；|
| NODE_SEPIA | 图像转换为深褐色比例属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：图像转换为深褐色比例，范围0-1之间，比如0.5指按照50%进行深褐色处理； <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：图像转换为深褐色比例，范围0-1之间；  |
| NODE_CONTRAST | 对比度属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：对比度，等于1时为原图，越大则对比度越高，取值范围：[0, 10)； <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：对比度，取值范围：[0, 10)；  |
| NODE_FOREGROUND_COLOR | 前景颜色属性，支持属性设置和属性获取接口。属性重置接口无效果。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式，支持两种入参格式：<br> 1：.value[0].u32：颜色数值，0xargb类型，如0xFFFF0000表示红色；<br> 2：.value[0].i32：颜色数值枚举ArkUI_ColoringStrategy；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：颜色数值，0xargb类型；|
| NODE_OFFSET | 组件子元素相对组件自身的额外偏移属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32 表示x轴方向的偏移值, 单位为vp。 <br> .value[1].f32 表示y轴方向的偏移值, 单位为vp。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32 表示x轴方向的偏移值, 单位为vp。 <br> .value[1].f32 表示y轴方向的偏移值, 单位为vp。|
| NODE_MARK_ANCHOR | 组件子元素在位置定位时的锚点属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32 表示锚点x坐标值, 单位为vp。 <br> .value[1].f32 表示锚点y坐标值, 单位为vp。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32 表示锚点x坐标值, 单位为vp。 <br> .value[1].f32 表示锚点y坐标值, 单位为vp。  |
| NODE_BACKGROUND_IMAGE_POSITION | 背景图在组件中显示位置，即相对于组件左上角的坐标，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32 表示x轴方向的位置, 单位为px。 <br> .value[1].f32 表示y轴方向的位置, 单位为px。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32 表示x轴方向的位置, 单位为px。 <br> .value[1].f32 表示y轴方向的位置, 单位为px。|
| NODE_ALIGN_RULES | 相对容器中子组件的对齐规则属性，支持属性设置，属性重置，获取属性接口。.object：使用[ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md)对象作为组件的对齐规则。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .object：使用[ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md)对象作为组件的对齐规则。 |
| NODE_ALIGN_SELF | 设置子组件在父容器交叉轴的对齐格式，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：设置子组件在父容器交叉轴的对齐格式类型， <br> 参数类型[ArkUI_ItemAlignment](capi-native-type-h.md#arkui_itemalignment)，默认值为ARKUI_ITEM_ALIGNMENT_AUTO。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：设置子组件在父容器交叉轴的对齐格式类型， <br> 参数类型[ArkUI_ItemAlignment](capi-native-type-h.md#arkui_itemalignment)，默认值为ARKUI_ITEM_ALIGNMENT_AUTO。 |
| NODE_FLEX_GROW | 设置组件在父容器的剩余空间所占比例，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：父容器的剩余空间所占比例。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：父容器的剩余空间所占比例。 |
| NODE_FLEX_SHRINK | 设置父容器压缩尺寸分配给此属性所在组件的比例，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：父容器压缩尺寸分配给此属性所在组件的比例数值。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：父容器压缩尺寸分配给此属性所在组件的比例数值。 |
| NODE_FLEX_BASIS | 设置组件的基准尺寸，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：组件在父容器主轴方向上的基准尺寸。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：组件在父容器主轴方向上的基准尺寸。 |
| NODE_ACCESSIBILITY_GROUP | 无障碍组属性, 支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].i32：为1时表示该组件及其所有子组件为一整个可以选中的组件。无障碍服务将不再关注其子组件内容。参数类型为1或者0。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：为1时表示该组件及其所有子组件为一整个可以选中的组件。无障碍服务将不再关注其子组件内容。参数类型为1或者0。|
| NODE_ACCESSIBILITY_TEXT | 无障碍文本属性，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .string：无障碍文本。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .string：无障碍文本。|
| NODE_ACCESSIBILITY_MODE | 无障碍辅助服务模式，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].i32：辅助服务模式，参数类型[ArkUI_AccessibilityMode](capi-native-type-h.md#arkui_accessibilitymode)。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：辅助服务模式，参数类型[ArkUI_AccessibilityMode](capi-native-type-h.md#arkui_accessibilitymode)。|
| NODE_ACCESSIBILITY_DESCRIPTION | 无障碍说明属性，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .string：无障碍说明。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .string：无障碍说明。|
| NODE_FOCUS_STATUS | 组件获取焦点属性，支持属性设置，属性获取。 |
| NODE_ASPECT_RATIO | 设置组件的宽高比，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：组件的宽高比，输入值为 width/height。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：组件的宽高比，width/height的比值。 |
| NODE_LAYOUT_WEIGHT | Row/Column/Flex 布局下的子组件布局权重参数，支持属性设置、属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].u32：子组件占主轴尺寸的权重。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].u32：子组件占主轴尺寸的权重。  |
| NODE_DISPLAY_PRIORITY | Row/Column/Flex(单行) 布局下的子组件在布局容器中显示的优先级，支持属性设置、属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].u32：子组件在父容器中的显示优先级。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].u32：子组件在父容器中的显示优先级。 |
| NODE_OUTLINE_WIDTH | 设置元素的外描边宽度。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：元素左边的外描边宽度。 <br> .value[1].f32：元素上边的外描边宽度。 <br> .value[2].f32：元素右边的外描边宽度。 <br> .value[3].f32：元素下边的外描边宽度。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：元素左边的外描边宽度。 <br> .value[1].f32：元素上边的外描边宽度。 <br> .value[2].f32：元素右边的外描边宽度。 <br> .value[3].f32：元素下边的外描边宽度。 |
| NODE_WIDTH_PERCENT | 宽度属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：宽度数值，单位为百分比；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：宽度数值，单位为百分比；|
| NODE_HEIGHT_PERCENT | 高度属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：高度数值，单位为百分比；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：高度数值，单位为百分比； |
| NODE_PADDING_PERCENT | 内间距属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：<br> 1：上下左右四个位置的内间距值相等。<br> .value[0].f32：内间距数值，单位为百分比；<br> 2：分别指定上下左右四个位置的内间距值。<br> .value[0].f32：上内间距数值，单位为百分比；<br> .value[1].f32：右内间距数值，单位为百分比；<br> .value[2].f32：下内间距数值，单位为百分比；<br> .value[3].f32：左内间距数值，单位为百分比；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：上内间距数值，单位为百分比；<br> .value[1].f32：右内间距数值，单位为百分比；<br> .value[2].f32：下内间距数值，单位为百分比；<br> .value[3].f32：左内间距数值，单位为百分比； |
| NODE_MARGIN_PERCENT | 外间距属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：<br> 1：上下左右四个位置的外间距值相等。<br> .value[0].f32：外间距数值，单位为百分比；<br> 2：分别指定上下左右四个位置的外间距值。<br> .value[0].f32：上外间距数值，单位为百分比；<br> .value[1].f32：右外间距数值，单位为百分比；<br> .value[2].f32：下外间距数值，单位为百分比；<br> .value[3].f32：左外间距数值，单位为百分比；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：上外间距数值，单位为百分比；<br> .value[1].f32：右外间距数值，单位为百分比；<br> .value[2].f32：下外间距数值，单位为百分比；<br> .value[3].f32：左外间距数值，单位为百分比； |
| NODE_GEOMETRY_TRANSITION | 组件内隐式共享元素转场，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0]?.i32：参数类型为1或者0。共享元素绑定的2个组件，针对出场元素未进行删除时是否要继续参与共享元素动画，默认为false，不参与保持原始位置不动。 <br> .string 用于设置绑定关系，id置""清除绑定关系避免参与共享行为，id可更换重新建立绑定关系。同一个id只能有两个组件绑定且是in/out不同类型角色，不能多个组件绑定同一个id。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：参数类型为1或者0。共享元素绑定的2个组件，针对出场元素未进行删除时是否要继续参与共享元素动画，默认未false，不参与保持原始位置不动。 <br> .string 用于设置绑定关系，id置""清除绑定关系避免参与共享行为，id可更换重新建立绑定关系。同一个id只能有两个组件绑定且是in/out不同类型角色，不能多个组件绑定同一个id。|
| NODE_RELATIVE_LAYOUT_CHAIN_MODE | 指定以该组件为链头所构成的链的参数，支持属性设置、属性重置和属性获取接口。仅当父容器为RelativeContainer时生效。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：链的方向。枚举[ArkUI_Axis](capi-native-type-h.md#arkui_axis)。 <br> .value[1].i32：链的样式。枚举[ArkUI_RelativeLayoutChainStyle](capi-native-type-h.md#arkui_relativelayoutchainstyle)。 <br> .value[0].i32：链的方向。枚举[ArkUI_Axis](capi-native-type-h.md#arkui_axis)。 <br> .value[1].i32：链的样式。枚举[ArkUI_RelativeLayoutChainStyle](capi-native-type-h.md#arkui_relativelayoutchainstyle)。|
| NODE_RENDER_FIT | 设置宽高动画过程中的组件内容填充方式，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32 内容填充方式，使用[ArkUI_RenderFit](capi-native-type-h.md)枚举值。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32 内容填充方式，使用[ArkUI_RenderFit](capi-native-type-h.md)枚举值。 |
| NODE_OUTLINE_COLOR | 外描边颜色属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> 1: .value[0].u32：统一设置四条边的边框颜色，使用0xargb表示，如0xFFFF11FF。 <br> 2: .value[0].u32：设置上侧边框颜色，使用0xargb表示，如0xFFFF11FF。 <br> .value[1].u32：设置右侧边框颜色，使用0xargb表示，如0xFFFF11FF。 <br> .value[2].u32：设置下侧边框颜色，使用0xargb表示，如0xFFFF11FF。 <br> .value[3].u32：设置左侧边框颜色，使用0xargb表示，如0xFFFF11FF。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].u32：设置上侧边框颜色，使用0xargb表示，如0xFFFF11FF。 <br> .value[1].u32：设置右侧边框颜色，使用0xargb表示，如0xFFFF11FF。 <br> .value[2].u32：设置下侧边框颜色，使用0xargb表示，如0xFFFF11FF。 <br> .value[3].u32：设置左侧边框颜色，使用0xargb表示，如0xFFFF11FF。 |
| NODE_SIZE | 设置高宽尺寸，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：宽度数值，单位为vp；<br> .value[1].f32：高度数值，单位为vp；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：宽度数值，单位为vp；<br> .value[1].f32：高度数值，单位为vp；|
| NODE_RENDER_GROUP | 设置当前组件和子组件是否先整体离屏渲染绘制后再与父控件融合绘制，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].i32：参数类型为1或者0。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：参数类型为1或者0。 |
| NODE_COLOR_BLEND | 为组件添加颜色叠加效果，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].u32：叠加的颜色，使用0xargb表示，如0xFFFF11FF。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].u32：叠加的颜色，使用0xargb表示，如0xFFFF11FF。  |
| NODE_FOREGROUND_BLUR_STYLE | 为当前组件提供内容模糊能力，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32 表示内容模糊样式，取[ArkUI_BlurStyle](capi-native-type-h.md#arkui_blurstyle)枚举值。<br> .value[1]?.i32 表示内容模糊效果使用的深浅色模式，取[ArkUI_ColorMode](capi-native-type-h.md#arkui_colormode)枚举值。<br> .value[2]?.i32 表示内容模糊效果使用的取色模式，取[ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor)枚举值。<br> .value[3]?.f32 表示模糊效果程度，取[0.0,1.0]范围内的值。<br> .value[4]?.i32 表示灰阶模糊参数，对黑色的提亮程度，取值范围为[0,127]。<br> .value[5]?.i32 表示灰阶模糊参数，对白色的压暗程度，取值范围为[0,127]。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32 表示内容模糊样式，取[ArkUI_BlurStyle](capi-native-type-h.md#arkui_blurstyle)枚举值。<br> .value[1].i32 表示内容模糊效果使用的深浅色模式，取[ArkUI_ColorMode](capi-native-type-h.md#arkui_colormode)枚举值。<br> .value[2].i32 表示内容模糊效果使用的取色模式，取[ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor)枚举值。<br> .value[3].f32 表示模糊效果程度，取[0.0,1.0]范围内的值。<br> .value[4].i32 表示灰阶模糊参数，对黑色的提亮程度，取值范围为[0,127]。<br> .value[5].i32 表示灰阶模糊参数，对白色的压暗程度，取值范围为[0,127]。 |
| NODE_LAYOUT_RECT | 组件布局大小位置属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：组件X轴坐标，单位为px；<br> .value[1].i32：组件Y轴坐标，单位为px；<br> .value[2].i32：组件宽度，单位为px；<br> .value[3].i32：组件高度，单位为px；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：组件X轴坐标，单位为px；<br> .value[1].i32：组件Y轴坐标，单位为px；<br> .value[2].i32：组件宽度，单位为px；<br> .value[3].i32：组件高度，单位为px；|
| NODE_FOCUS_ON_TOUCH | 设置当前组件是否支持点击获焦能力，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].i32：参数类型为1或者0。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：参数类型为1或者0。|
| NODE_BORDER_WIDTH_PERCENT = 85 | 边框宽度属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> 1: .value[0].f32：统一设置四条边的边框宽度，单位为百分比。 <br> 2: .value[0].f32：设置上边框的边框宽度，单位为百分比。 <br> .value[1].f32：设置右边框的边框宽度，单位为百分比。 <br> .value[2].f32：设置下边框的边框宽度，单位为百分比。 <br> .value[3].f32：设置左边框的边框宽度，单位为百分比。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：设置上边框的边框宽度，单位为百分比。 <br> .value[1].f32：设置右边框的边框宽度，单位为百分比。 <br> .value[2].f32：设置下边框的边框宽度，单位为百分比。 <br> .value[3].f32：设置左边框的边框宽度，单位为百分比。  |
| NODE_BORDER_RADIUS_PERCENT = 86 | 边框圆角属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> 1: .value[0].f32：统一设置四条边的边框圆角半径，单位为百分比。 <br> 2: .value[0].f32：设置左上角圆角半径，单位为百分比。 <br> .value[1].f32：设置右上角圆角半径，单位为百分比。 <br> .value[2].f32：设置左下角圆角半径，单位为百分比。 <br> .value[3].f32：设置右下角圆角半径，单位为百分比。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：设置左上角圆角半径，单位为百分比。 <br> .value[1].f32：设置右上角圆角半径，单位为百分比。 <br> .value[2].f32：设置左下角圆角半径，单位为百分比。 <br> .value[3].f32：设置右下角圆角半径，单位为百分比。  |
| NODE_ACCESSIBILITY_ID = 87 | 无障碍自定义标识ID，支持属性获取。属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：无障碍自定义标识ID。 |
| NODE_ACCESSIBILITY_ACTIONS = 88 | 定义无障碍支持操作类型属性，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].u32：配置无障碍操作类型，参数类型[ArkUI_AccessibilityActionType](capi-native-type-h.md#arkui_accessibilityactiontype)。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].u32：配置无障碍操作类型，参数类型[ArkUI_AccessibilityActionType](capi-native-type-h.md#arkui_accessibilityactiontype)。 |
| NODE_ACCESSIBILITY_ROLE = 89 | 定义无障碍组件类型属性，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].u32：无障碍组件类型，参数类型[ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype)。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].u32：无障碍组件类型，参数类型[ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype)。 |
| NODE_ACCESSIBILITY_STATE = 90 | 定义无障碍状态属性，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .object：参数类型为[ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md)。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .object：参数类型为[ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md)。  |
| NODE_ACCESSIBILITY_VALUE = 91 | 定义无障碍信息属性，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .object：参数类型为[ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .object：参数类型为[ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)。 |
| NODE_EXPAND_SAFE_AREA = 92 | 定义控制组件扩展其安全区域，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0]?.u32：扩展安全区域的枚举值集合[ArkUI_SafeAreaType](capi-native-type-h.md#arkui_safeareatype)，例如：ARKUI_SAFE_AREA_TYPE_SYSTEM |
| NODE_VISIBLE_AREA_CHANGE_RATIO = 93 | 定义控制组件触发可视区域面积变更事件的可视区域面积占组件本身面积的比例阈值。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[...].f32：占比数值，输入范围0-1。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[...].f32：占比数值； |
| NODE_TRANSITION = 94 | 定义组件插入和删除时显示过渡动效，支持属性设置，属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .object：参数类型为[ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .object：参数类型为[ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)。  |
| NODE_UNIQUE_ID = 95 | 组件标识ID，支持属性获取。|
| NODE_FOCUS_BOX = 96 | 设置当前组件系统焦点框样式。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32: 焦点框相对组件边缘的距离。 <br> 正数代表外侧，负数代表内侧。 <br> 不支持百分比。 <br> .value[1].f32: 焦点框宽度。 不支持负数和百分比。 <br> .value[2].u32: 焦点框颜色。 |
| NODE_CLICK_DISTANCE = 97 | 组件所绑定的点击手势移动距离限制，支持属性设置。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32 表示识别点击手势时允许手指在该范围内移动，单位为vp。  |
| NODE_TAB_STOP = 98 | 控制焦点是否能停在当前组件，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].i32：参数类型为1或者0。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：参数类型为1或者0。<br>**起始版本：** 14  |
| NODE_BACKDROP_BLUR = 99 | 设置背景模糊效果，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].f32：表示背景模糊半径，取值范围[0,+∞)。单位px，默认值0.0。<br> .value[1]?.f32：表示灰阶模糊参数，对黑色的提亮程度，取值范围为[0,127]。<br> .value[2]?.f32：表示灰阶模糊参数，对白色的压暗程度，取值范围为[0,127]。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：表示背景模糊半径，取值范围[0,+∞)。单位px。<br> .value[1].f32：表示灰阶模糊参数，对黑色的提亮程度，取值范围为[0,127]。<br> .value[2].f32：表示灰阶模糊参数，对白色的压暗程度，取值范围为[0,127]。<br>**起始版本：** 15 |
| NODE_BACKGROUND_IMAGE_RESIZABLE_WITH_SLICE = 100 | 设置背景图在拉伸时可调整大小的属性，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].f32: 图片左部拉伸时，图片的像素值保持不变，单位为vp。 <br> .value[1].f32: 图片顶部拉伸时，图片的像素值保持不变，单位为vp。 <br> .value[2].f32: 图片右部拉伸时，图片的像素值保持不变，单位为vp。 <br> .value[3].f32: 图片底部拉伸时，图片的像素值保持不变，单位为vp。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32: 图片左部拉伸时，图片的像素值保持不变，单位为vp。 <br> .value[1].f32: 图片顶部拉伸时，图片的像素值保持不变，单位为vp。 <br> .value[2].f32: 图片右部拉伸时，图片的像素值保持不变，单位为vp。 <br> .value[3].f32: 图片底部拉伸时，图片的像素值保持不变，单位为vp。 <br>**起始版本：** 19 |
| NODE_NEXT_FOCUS = 101 | 设置下一个走焦节点。[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)的参数格式： <br> .value[0].i32：走焦类型，定义在 [ArkUI_FocusMove](capi-native-type-h.md#arkui_focusmove)。.object: 下一个焦点。 [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。<br>**起始版本：** 18 |
| NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_RATIO = 102 | 设置可见区域变化监听的参数。<br>**起始版本：** 17  |
| NODE_TRANSLATE_WITH_PERCENT = 103 | 设置组件平移，支持百分比形式的平移入参，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32： x轴移动距离，默认单位为百分比，除非value[3]存在且value[3]为0时单位为vp，默认值0；<br> .value[1].f32： y轴移动距离，默认单位为百分比，除非value[4]存在且value[4]为0时单位为vp，默认值0；<br> .value[2].f32： z轴移动距离，单位vp，默认值0。<br> .value[3]?.i32： x轴移动距离是否为百分比形式指定，取值范围：0或1。为1时表示以百分比形式指定，例如value[0].f32=0.1且value[3].i32=1时表示x方向平移10%。默认值1。<br> .value[4]?.i32： y轴移动距离是否为百分比形式指定，取值范围：0或1。为1时表示以百分比形式指定，例如value[1].f32=0.1且value[4].i32=1时表示y方向平移10%，默认值1。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32： x轴移动距离，单位取决于value[3]；<br> .value[1].f32： y轴移动距离，单位取决于value[4]；<br> .value[2].f32： z轴移动距离，单位vp；<br> .value[3].i32： x轴移动距离的单位是否为百分比，当value[3].i32为0时x轴移动距离单位为vp，当value[3].i32为1时x轴移动距离单位为百分比；<br> .value[4].i32： y轴移动距离的单位是否为百分比，当value[4].i32为0时y轴移动距离单位为vp，当value[4].i32为1时y轴移动距离单位为百分比；<br>**起始版本：** 20  |
| NODE_ROTATE_ANGLE = 104 | 设置组件旋转，支持各轴旋转角属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32： x轴方向旋转角度，默认值0；<br> .value[1].f32： y轴方向旋转角度，默认值0；<br> .value[2].f32： z轴方向旋转角度，默认值0；<br> .value[3].f32： 视距，即视点到z=0平面的距离，单位px，默认值0。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32： x轴方向旋转角度，默认值0；<br> .value[1].f32： y轴方向旋转角度，默认值0；<br> .value[2].f32： z轴方向旋转角度，默认值0；<br> .value[3].f32： 视距，即视点到z=0平面的距离，单位px，默认值0。<br>**起始版本：** 20  |
| NODE_TEXT_CONTENT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT | text组件设置文本内容属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string 表示文本内容。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string 表示文本内容。|
| NODE_FONT_COLOR | 组件字体颜色属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：字体颜色数值，0xargb格式，形如 0xFFFF0000 表示红色；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：字体颜色数值，0xargb格式；|
| NODE_FONT_SIZE | 组件字体大小属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：字体大小数值，单位为fp；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：字体大小数值，单位为fp；|
| NODE_FONT_STYLE | 组件字体样式属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：字体样式[ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle)，默认值为ARKUI_FONT_STYLE_NORMAL；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：字体样式[ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle)； |
| NODE_FONT_WEIGHT | 组件字体粗细属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：字体粗细样式[ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight)，默认值为ARKUI_FONT_WEIGHT_NORMAL；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：字体粗细样式[ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight)；|
| NODE_TEXT_LINE_HEIGHT | 文本行高属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32 表示lineHeight值，单位为fp。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32 表示lineHeight值，单位为fp。 |
| NODE_TEXT_DECORATION | 置文本装饰线样式及其颜色属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：文本装饰线类型[ArkUI_TextDecorationType](capi-native-type-h.md#arkui_textdecorationtype)，默认值为ARKUI_TEXT_DECORATION_TYPE_NONE；<br> .value[1]?.u32：可选值，装饰线颜色，0xargb格式，形如 0xFFFF0000 表示红色；<br> .value[2]?.i32：文本装饰线样式[ArkUI_TextDecorationStyle](capi-native-type-h.md#arkui_textdecorationstyle)；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：文本装饰线类型[ArkUI_TextDecorationType](capi-native-type-h.md#arkui_textdecorationtype)；<br> .value[1].u32：装饰线颜色，0xargb格式。<br> .value[2].i32：文本装饰线样式[ArkUI_TextDecorationStyle](capi-native-type-h.md#arkui_textdecorationstyle)；|
| NODE_TEXT_CASE | 文本大小写属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：表示文本大小写类型[ArkUI_TextCase](capi-native-type-h.md#arkui_textcase)，默认值为ARKUI_TEXT_CASE_NORMAL。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：表示文本大小写类型[ArkUI_TextCase](capi-native-type-h.md#arkui_textcase)。  |
| NODE_TEXT_LETTER_SPACING | 文本字符间距属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32 表示字符间距值，单位为fp。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32 表示字符间距值，单位为fp。  |
| NODE_TEXT_MAX_LINES | 文本最大行数属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32 表示最大行数。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32 表示最大行数。  |
| NODE_TEXT_ALIGN | 文本水平对齐方式, 支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：表示文本水平对齐方式，取[ArkUI_TextAlignment](capi-native-type-h.md#arkui_textalignment)枚举值。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：表示文本水平对齐方式，取[ArkUI_TextAlignment](capi-native-type-h.md#arkui_textalignment)枚举值。|
| NODE_TEXT_OVERFLOW | 文本超长时的显示方式属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：表示文本超长时的显示方式。[ArkUI_TextOverflow](capi-native-type-h.md)<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：表示文本超长时的显示方式。[ArkUI_TextOverflow](capi-native-type-h.md)|
| NODE_FONT_FAMILY | Text字体列表属性，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .string：字体字符串，多个用,分隔。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .string：字体字符串，多个用,分隔。|
| NODE_TEXT_COPY_OPTION | 文本复制粘贴属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：复制粘贴方式[ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions)，默认值为ARKUI_COPY_OPTIONS_NONE；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：复制粘贴方式[ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions)。 |
| NODE_TEXT_BASELINE_OFFSET | 文本基线的偏移量属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：偏移量数值，单位为fp；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：偏移量数值，单位为fp。 |
| NODE_TEXT_TEXT_SHADOW | 文字阴影效果属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：阴影模糊半径，单位为vp；<br> .value[1].i32：阴影类型[ArkUI_ShadowType](capi-native-type-h.md#arkui_shadowtype)，默认值为ARKUI_SHADOW_TYPE_COLOR；<br> .value[2].u32：阴影颜色，0xargb格式，形如 0xFFFF0000 表示红色；<br> .value[3].f32：阴影X轴偏移量，单位为vp；<br> .value[4].f32：阴影Y轴偏移量，单位为vp；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：阴影模糊半径，单位为vp；<br> .value[1].i32：阴影类型[ArkUI_ShadowType](capi-native-type-h.md#arkui_shadowtype)；<br> .value[2].u32：阴影颜色，0xargb格式；<br> .value[3].f32：阴影X轴偏移量，单位为vp；<br> .value[4].f32：阴影Y轴偏移量，单位为vp； |
| NODE_TEXT_MIN_FONT_SIZE | Text最小显示字号，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].f32：文本最小显示字号，单位FP。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：文本最小显示字号，单位FP。  |
| NODE_TEXT_MAX_FONT_SIZE | Text最大显示字号，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].f32：文本最大显示字号 单位FP。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：文本最大显示字号 单位FP。  |
| NODE_TEXT_FONT | Text样式，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .string?：可选值 字体列表，使用多个字体，使用','进行分割。 <br> .value[0].f32：文本尺寸 单位FP。 <br> .value[1]?.i32：可选值，文本的字体粗细，参数类型[ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight)。默认值为ARKUI_FONT_WEIGHT_NORMAL。 <br> .value[2]?.i32：可选值，字体样式，参数类型[ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle)。默认值为ARKUI_FONT_STYLE_NORMAL。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .string：字体列表，使用多个字体，使用','进行分割。 <br> .value[0].f32：文本尺寸 单位FP。 <br> .value[1].i32：文本的字体粗细，参数类型[ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight)。默认值为ARKUI_FONT_WEIGHT_NORMAL。 <br> .value[2].i32：字体样式，参数类型[ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle)。默认值为ARKUI_FONT_STYLE_NORMAL。|
| NODE_TEXT_HEIGHT_ADAPTIVE_POLICY | Text自适应高度的方式，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].i32：参数类型[ArkUI_TextHeightAdaptivePolicy](capi-native-type-h.md#arkui_textheightadaptivepolicy)。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：参数类型[ArkUI_TextHeightAdaptivePolicy](capi-native-type-h.md#arkui_textheightadaptivepolicy)。|
| NODE_TEXT_INDENT | 文本首行缩进属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32: 表示首行缩进值。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32: 表示首行缩进值。<br> |
| NODE_TEXT_WORD_BREAK | 文本断行规则属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32: 参数类型[ArkUI_WordBreak](capi-native-type-h.md#arkui_wordbreak)。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32: 参数类型[ArkUI_WordBreak](capi-native-type-h.md#arkui_wordbreak)。 |
| NODE_TEXT_ELLIPSIS_MODE | 设置文本省略位置，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32: 参数类型[ArkUI_EllipsisMode](capi-native-type-h.md#arkui_ellipsismode)。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32: 参数类型[ArkUI_EllipsisMode](capi-native-type-h.md#arkui_ellipsismode)。  |
| NODE_TEXT_LINE_SPACING | 文本行间距属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32 表示lineSpacing值，单位为fp。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32 表示lineSpacing值，单位为fp。  |
| NODE_FONT_FEATURE | 设置文本特性效果，设置NODE_FONT_FEATURE属性，NODE_FONT_FEATURE是 OpenType 字体的高级排版能力，如支持连字、数字等宽等特性，一般用在自定义字体中，其能力需要字体本身支持,支持属性设置，属性重置，属性获取接口。 <br>     <br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .string 符合文本特性格式的字符串，格式为normal  \|  \<feature-tag-value>, <br>  \<feature-tag-value>的格式为：<string\>  [ <integer\>  \| on  \| off ], <br>  \<feature-tag-value>的个数可以有多个，中间用','隔开,例如，使用等宽数字的输入格式为：ss01 on。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .string 表示文本特性的内容，多个文本特性之间使用逗号分隔。 <br> |
| NODE_TEXT_ENABLE_DATA_DETECTOR | 设置使能文本识别。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：使能文本识别，默认值false。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：使能文本识别。 |
| NODE_TEXT_ENABLE_DATA_DETECTOR_CONFIG | 设置文本识别配置。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0...].i32: 实体类型数组，参数类型[ArkUI_TextDataDetectorType](capi-native-type-h.md#arkui_textdatadetectortype)。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0...].i32：实体类型数组，参数类型[ArkUI_TextDataDetectorType](capi-native-type-h.md#arkui_textdatadetectortype)。  |
| NODE_TEXT_SELECTED_BACKGROUND_COLOR | 文本选中时的背景色属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].u32：颜色数值，0xargb格式，形如 0xFFFF0000 表示红色。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].u32：颜色数值，0xargb格式。 |
| NODE_TEXT_CONTENT_WITH_STYLED_STRING | text组件使用格式化字符串对象设置文本内容属性，支持属性设置，属性重置，属性获取接口。配置自定义OH_Drawing_Typography对象到text组件，会跳过文本控件的布局测算阶段，需要注意： <br> 1、需要保证OH_ArkUI_StyledString对象、OH_Drawing_Typography对象的生命周期跟随Text组件生命周期，Text组件析构时重置OH_ArkUI_StyledString对象，否则会导致应用出现空指针崩溃。 <br> 2、保证OH_Drawing_TypographyLayout方法调用时序在Text组件的布局测算之前。 <br> 3、释放OH_ArkUI_StyledString对象、OH_Drawing_Typography对象时，需要同步调用Text组件的reset方法，否则会导致应用出现空指针崩溃。 <br>     <br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .object 表示 ArkUI_StyledString 格式化字符串数据，参数类型为[ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .object 表示 ArkUI_StyledString 格式化字符串数据，参数类型为[ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)。 |
| NODE_TEXT_HALF_LEADING = 1029 | text组件设置文本纵向居中显示。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：文本是否纵向居中显示，默认值false。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：文本是否纵向居中显示。 <|
| NODE_IMMUTABLE_FONT_WEIGHT = 1030 | 组件字体粗细属性，支持属性设置，属性重置和属性获取接口。通过此接口设置的粗细属性不会跟随系统字体粗细变化。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：字体粗细样式[ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight)，默认值为ARKUI_FONT_WEIGHT_NORMAL； <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：字体粗细样式[ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight)； <br>**起始版本：** 15  |
| NODE_TEXT_LINE_COUNT = 1031 | 文本行数属性，支持属性获取。属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32: 表示文本行数。 <br>**起始版本：** 20  |
| NODE_TEXT_OPTIMIZE_TRAILING_SPACE = 1032 | 设置文本排版时是否优化每行结尾的空格，支持属性设置，属性重置，属性获取接口.<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> value[0].i32: 设置文本排版时是否优化每行结尾的空格，默认值为false. <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> value[0].i32: 文本排版时是否优化每行结尾的空格。 <br>**起始版本：** 20  |
| NODE_TEXT_LINEAR_GRADIENT = 1033 | 设置文本线性渐变效果，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：线性渐变的起始角度。当direction属性设置为ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM时，angle属性生效；否则，以direction属性为主要布局方式。0点方向顺时针旋转为正向角度，默认值：180 <br> .value[1].i32：线性渐变的方向[ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection)。设置除ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM之外的线性渐变方向后，angle不生效。默认值：ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT_BOTTOM <br> .value[2].i32：为渐变的颜色重复着色，false表示不重复着色，true表示重复着色。默认值：false <br> .object: 参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过。 <br> colors：渐变色颜色数组，数组元素为0xargb格式，形如0xFFFF0000表示红色。 <br> stops：stops表示指定颜色所处位置的数组，数组元素取值范围为[0,1.0]，0表示需要设置渐变色的容器的开始处，1.0表示容器的结尾处。想要实现多个颜色渐变效果时，数组元素建议递增设置，如后一个数组元素比前一个数组元素小的话，按照等于前一个数组元素的值处理。 <br> size：颜色个数，若小于colors数组长度则仅生效前size个颜色，不建议设置大于colors数组长度或小于等于0的值以及异常值。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：线性渐变的起始角度。当为ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM时，angle为设置值，其他情况均为默认值0。 <br> .value[1].i32：线性渐变的方向[ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection)。 <br> .value[2].i32：为渐变的颜色重复着色，0表示不重复着色，1表示重复着色。默认值：0 <br> .object：参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过： <br> colors：渐变色颜色数组，数组元素为0xargb格式，形如0xFFFF0000表示红色。 <br> stops：stops表示指定颜色所处位置的数组，数组元素取值范围为[0,1.0]，0表示需要设置渐变色的容器的开始处，1.0表示容器的结尾处。 <br> size：生效后渐变色的颜色个数。 <br>**起始版本：** 20 |
| NODE_TEXT_RADIAL_GRADIENT = 1034 | 设置文本径向渐变渐变效果，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0]?.f32：为径向渐变的中心点，即相对于当前文本框左上角的X轴坐标。 <br> .value[1]?.f32：为径向渐变的中心点，即相对于当前文本框左上角的Y轴坐标。文本框左上角的坐标为[0,0]。<br> .value[2]?.f32：径向渐变的半径，默认值0。 <br> .value[3]?.i32：为渐变的颜色重复着色，false表示不重复着色，true表示重复着色。默认值：false <br> .object：参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过： <br> colors：渐变色颜色数组，数组元素为0xargb格式，形如0xFFFF0000表示红色。 <br> stops：stops表示指定颜色所处位置的数组，数组元素取值范围为[0,1.0]，0表示需要设置渐变色的容器的开始处，1.0表示容器的结尾处。想要实现多个颜色渐变效果时，数组元素建议递增设置，如后一个数组元素比前一个数组元素小的话，按照等于前一个数组元素的值处理。 <br> size：颜色个数，若小于colors数组长度则仅生效前size个颜色，不建议设置大于colors数组长度或小于等于0的值以及异常值。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0]?.f32：为径向渐变的中心点，即相对于当前文本框左上角的X轴坐标。 <br> .value[1]?.f32：为径向渐变的中心点，即相对于当前文本框左上角的Y轴坐标。文本框左上角的坐标为[0,0]。<br> .value[2]?.f32：径向渐变的半径，默认值0。 <br> .value[3]?.i32：为渐变的颜色重复着色，0表示不重复着色，1表示重复着色。默认值：0 <br> .object：参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过： <br> colors：渐变色颜色数组，数组元素为0xargb格式，形如0xFFFF0000表示红色。 <br> stops：stops表示指定颜色所处位置的数组，数组元素取值范围为[0,1.0]，0表示需要设置渐变色的容器的开始处，1.0表示容器的结尾处。 <br> size：生效后渐变色的颜色个数。 <br>**起始版本：** 20  |
| NODE_TEXT_VERTICAL_ALIGN = 1035 | 设置文本内容垂直对齐方式，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：文本内容垂直对齐方式[ArkUI_TextVerticalAlignment](capi-native-type-h.md#arkui_textverticalalignment)，默认值：ARKUI_TEXT_VERTICAL_ALIGNMENT_BASELINE <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：文本内容垂直对齐方式[ArkUI_TextVerticalAlignment](capi-native-type-h.md#arkui_textverticalalignment)。 <br>**起始版本：** 20   |
| NODE_SPAN_CONTENT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SPAN | 文本内容属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .string 表示span的文本内容。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .string 表示span的文本内容。  |
| NODE_SPAN_TEXT_BACKGROUND_STYLE | 文本背景色属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].u32 表示文本背景颜色，0xargb格式，形如0xFFFF0000 表示红色。 <br> 第二个参数为文本背景圆角设置，支持如下两种设置方式： <br> 1：.value[1].f32：四个方向的圆角半径统一设置，单位为vp。 <br> 2: .value[1].f32：设置左上角圆角半径，单位为vp。 <br> .value[2].f32：设置右上角圆角半径，单位为vp。 <br> .value[3].f32：设置左下角圆角半径，单位为vp。 <br> .value[4].f32：设置右下角圆角半径，单位为vp。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].u32：文本背景颜色，0xargb格式。 <br> .value[1].f32：左上角圆角半径，单位为vp。 <br> .value[2].f32：右上角圆角半径，单位为vp。 <br> .value[3].f32：左下角圆角半径，单位为vp。 <br> .value[4].f32：右下角圆角半径，单位为vp。 |
| NODE_SPAN_BASELINE_OFFSET | 文本基线的偏移量属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：偏移量数值，单位为fp； <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：偏移量数值，单位为fp。  |
| NODE_IMAGE_SPAN_SRC = MAX_NODE_SCOPE_NUM * ARKUI_NODE_IMAGE_SPAN | imageSpan组件图片地址属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .string 表示imageSpan的图片地址。 <br> .object 表示 PixelMap 图片数据，参数类型为[ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .string 表示imageSpan的图片地址。 <br> .object 表示 PixelMap 图片数据，参数类型为[ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)；.object参数和.string参数二选一，不可同时设置。 |
| NODE_IMAGE_SPAN_VERTICAL_ALIGNMENT | 图片基于文本的对齐方式属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32 表示图片基于文本的对齐方式，取[ArkUI_ImageSpanAlignment](capi-native-type-h.md#arkui_imagespanalignment)枚举值。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32 表示图片基于文本的对齐方式，取[ArkUI_ImageSpanAlignment](capi-native-type-h.md#arkui_imagespanalignment)枚举值。  |
| NODE_IMAGE_SPAN_ALT | imageSpan组件占位图地址属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .string 表示image组件占位图地址(不支持gif类型图源)。 <br> .object 表示 PixelMap 图片数据，参数类型为[ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)；.object参数和.string参数二选一，不可同时设置。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .string 表示image组件占位图地址。 <br> .object 表示 PixelMap 图片数据，参数类型为[ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)。 |
| NODE_IMAGE_SPAN_BASELINE_OFFSET = 3003 | imageSpan组件的基线偏移量属性，支持属性设置，属性重置和属性获取接口。偏移量数值为正数时向上偏移，负数时向下偏移，默认值0，单位为fp。 <br>     <br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：偏移量数值，单位为fp； <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：偏移量数值，单位为fp。 <br>**起始版本：** 13  |
| NODE_IMAGE_SRC = MAX_NODE_SCOPE_NUM * ARKUI_NODE_IMAGE | image组件设置图片地址属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string 表示image组件地址。 <br> .object 表示 PixelMap 图片数据，参数类型为[ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)；.object参数和.string参数二选一，不可同时设置。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string 表示image组件地址。 <br> .object 表示 PixelMap 图片数据，参数类型为[ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)。|
| NODE_IMAGE_OBJECT_FIT | 图片填充效果属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32 表示图片填充效果，取[ArkUI_ObjectFit](capi-native-type-h.md#arkui_objectfit)枚举值。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32 表示图片填充效果，取[ArkUI_ObjectFit](capi-native-type-h.md#arkui_objectfit)枚举值。|
| NODE_IMAGE_INTERPOLATION | 图片插值效果效果属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32 表示插值效果效果，取[ArkUI_ImageInterpolation](capi-native-type-h.md#arkui_imageinterpolation)枚举值。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32 表示插值效果效果，取[ArkUI_ImageInterpolation](capi-native-type-h.md#arkui_imageinterpolation)枚举值。  |
| NODE_IMAGE_OBJECT_REPEAT | 图片重复样式属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32 表示图片重复样式，取[ArkUI_ImageRepeat](capi-native-type-h.md#arkui_imagerepeat)枚举值。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32 表示图片重复样式，取[ArkUI_ImageRepeat](capi-native-type-h.md#arkui_imagerepeat)枚举值。  |
| NODE_IMAGE_COLOR_FILTER | 图片滤镜效果属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32 ~ .value[19].f32 表示滤镜矩阵数组。 <br> .size  表示滤镜数组大小 5*4。 <br> .object 颜色滤波器指针，参数类型为OH_Drawing_ColorFilter，.object和.size参数只能二选一，不可同时设置。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32 ~ .value[19].f32 表示滤镜矩阵数组。 <br> .size  表示滤镜数组大小 5*4。 <br> .object 颜色滤波器指针，参数类型为OH_Drawing_ColorFilter。  |
| NODE_IMAGE_AUTO_RESIZE | 图源自动缩放属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32 表示是否缩放布尔值。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32 表示是否缩放布尔值。 |
| NODE_IMAGE_ALT | 占位图地址属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string 表示image组件占位图地址。<br> .object 表示 PixelMap 图片数据，参数类型为[ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)；.object参数和.string参数二选一，不可同时设置。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string 表示image组件占位图地址。<br> .object 表示 PixelMap 图片数据，参数类型为[ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)。 |
| NODE_IMAGE_DRAGGABLE | 图片拖拽效果属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32 表示是否支持拖拽，设置为true表示支持。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32 表示是否支持拖拽。 |
| NODE_IMAGE_RENDER_MODE | 图片渲染模式属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32 参数类型[ArkUI_ImageRenderMode](capi-native-type-h.md#arkui_imagerendermode)。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32 参数类型[ArkUI_ImageRenderMode](capi-native-type-h.md#arkui_imagerendermode)。 |
| NODE_IMAGE_FIT_ORIGINAL_SIZE | 设置图片的显示尺寸是否跟随图源尺寸，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32，设置图片的显示尺寸是否跟随图源尺寸，1表示跟随，0表示不跟随，默认值为0。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32，1表示图片的显示尺寸跟随图源尺寸，0表示图片的显示尺寸不跟随图源尺寸。 |
| NODE_IMAGE_FILL_COLOR | 设置填充颜色，设置后填充颜色会覆盖在图片上，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：填充色数值，0xargb格式，形如 0xFFFF0000 表示红色。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：填充色数值，0xargb格式。|
| NODE_IMAGE_RESIZABLE | 设置图像拉伸时，可调整大小的图像选项。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32 图片左部拉伸时，保持不变距离。单位vp。<br> .value[1].f32 图片上部拉伸时，保持不变距离。单位vp。<br> .value[2].f32 图片右部拉伸时，保持不变距离。单位vp。<br> .value[3].f32 图片下部拉伸时，保持不变距离。单位vp。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32 图片左部拉伸时，保持不变距离。单位vp。<br> .value[1].f32 图片上部拉伸时，保持不变距离。单位vp。<br> .value[2].f32 图片右部拉伸时，保持不变距离。单位vp。<br> .value[3].f32 图片下部拉伸时，保持不变距离。单位vp。 |
| NODE_IMAGE_SYNC_LOAD = 4012 | 图源同步加载属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32 表示是否同步。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32 表示是否同步。<br>**起始版本：** 20  |
| NODE_TOGGLE_SELECTED_COLOR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TOGGLE | 组件打开状态的背景颜色属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：背景色数值，0xargb格式，形如 0xFFFF0000 表示红色。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：背景色数值，0xargb格式。 |
| NODE_TOGGLE_SWITCH_POINT_COLOR | Switch类型的圆形滑块颜色属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：圆形滑块颜色数值，0xargb格式，形如 0xFFFF0000 表示红色。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：圆形滑块颜色数值，0xargb格式。 |
| NODE_TOGGLE_VALUE | Switch类型的开关值，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：设置开关的值，true表示开启。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：设置开关的值。|
| NODE_TOGGLE_UNSELECTED_COLOR | 组件关闭状态的背景颜色属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：背景色数值，0xargb格式，形如 0xFFFF0000 表示红色。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：背景色数值，0xargb格式。 |
| NODE_LOADING_PROGRESS_COLOR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_LOADING_PROGRESS | 加载进度条前景色属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：前景颜色数值，0xargb格式，形如 0xFFFF0000 表示红色。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：前景颜色数值，0xargb格式。 |
| NODE_LOADING_PROGRESS_ENABLE_LOADING | LoadingProgress动画显示属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：false时不显示动画，true时可以显示动画；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：0时不显示动画，1时可以显示动画。 |
| NODE_TEXT_INPUT_PLACEHOLDER = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_INPUT | 单行文本输入框的默认提示文本内容属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string：默认提示文本的内容。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string：默认提示文本的内容。 |
| NODE_TEXT_INPUT_TEXT | 单行文本输入框的默认文本内容属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string：默认文本的内。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string：默认文本的内容。 |
| NODE_TEXT_INPUT_CARET_COLOR | 光标颜色属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：光标颜色数值，0xargb格式，形如 0xFFFF0000 表示红色；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：光标颜色数值，0xargb格式。 |
| NODE_TEXT_INPUT_CARET_STYLE | 光标风格属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：光标宽度数值，单位为vp；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：光标宽度数值，单位为vp。 |
| NODE_TEXT_INPUT_SHOW_UNDERLINE | 单行文本输入框下划线属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：false表示不展示下划线，true表示展示下划线；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：0表示不展示下划线，1表示展示下划线。 |
| NODE_TEXT_INPUT_MAX_LENGTH | 输入框支持的最大文本数属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：最大文本数的数字，无单位。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：最大文本数的数字。|
| NODE_TEXT_INPUT_ENTER_KEY_TYPE | 回车键类型属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：回车键类型枚举[ArkUI_EnterKeyType](capi-native-type-h.md#arkui_enterkeytype)，默认值为ARKUI_ENTER_KEY_TYPE_DONE。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：回车键类型枚举[ArkUI_EnterKeyType](capi-native-type-h.md#arkui_enterkeytype)。 |
| NODE_TEXT_INPUT_PLACEHOLDER_COLOR | 无输入时默认提示文本的颜色属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：颜色数值，0xargb格式，形如 0xFFFF0000 表示红色。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：颜色数值，0xargb格式。|
| NODE_TEXT_INPUT_PLACEHOLDER_FONT | 无输入时默认提示文本的字体配置（包括大小、字重、样式、字体列表）属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0]?.f32：可选字体大小数值，默认值16.0，单位为fp；<br> .value[1]?.i32：可选字体样式[ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle)，默认值为ARKUI_FONT_STYLE_NORMAL；<br> .value[2]?.i32：可选字体粗细样式[ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight)，默认值为ARKUI_FONT_WEIGHT_NORMAL；<br> ?.string: 字体族内容，多个字体族之间使用逗号分隔，形如“字重；字体族1，字体族2”。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：字体大小数值，单位为fp；<br> .value[1].i32：字体样式[ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle)；<br> .value[2].i32：字体粗细样式[ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight)；<br> .string: 字体族内容，多个字体族之间使用逗号分隔。|
| NODE_TEXT_INPUT_ENABLE_KEYBOARD_ON_FOCUS | 聚焦时是否绑定输入法属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：false表示聚焦不拉起输入法，true表示拉起。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：0表示聚焦不拉起输入法，1表示拉起。|
| NODE_TEXT_INPUT_TYPE | 输入框的类型属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：输入框类型枚举[ArkUI_TextInputType](capi-native-type-h.md#arkui_textinputtype)，默认值为ARKUI_TEXTINPUT_TYPE_NORMAL。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：输入框类型枚举[ArkUI_TextInputType](capi-native-type-h.md#arkui_textinputtype)。 |
| NODE_TEXT_INPUT_SELECTED_BACKGROUND_COLOR | 输入框文本选中时的背景色属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：颜色数值，0xargb格式，形如 0xFFFF0000 表示红色。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：颜色数值，0xargb格式。|
| NODE_TEXT_INPUT_SHOW_PASSWORD_ICON | 密码输入模式时是否显示末尾图标属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：false表示不显示图标，true表示显示图标；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：0表示不显示图标，1表示显示图标。 |
| NODE_TEXT_INPUT_EDITING | 控制单行文本输入框编辑态属性，支持属性设置。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：false表示退出编辑态，true表示维持现状。<br> 属性获取方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：false表示退出编辑态，true表示维持现状。  |
| NODE_TEXT_INPUT_CANCEL_BUTTON | 单行文本右侧清除按钮样式属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：按钮样式[ArkUI_CancelButtonStyle](capi-native-type-h.md#arkui_cancelbuttonstyle)，默认值为ARKUI_CANCELBUTTON_STYLE_INPUT；<br> .value[1]?.f32：图标大小数值，单位为vp；<br> .value[2]?.u32：按钮图标颜色数值，0xargb格式，形如 0xFFFF0000 表示红色；<br> ?.string：按钮图标地址，入参内容为图片本地地址，例如 /pages/icon.png。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：按钮样式[ArkUI_CancelButtonStyle](capi-native-type-h.md#arkui_cancelbuttonstyle)；<br> .value[1].f32：图标大小数值，单位为vp；<br> .value[2].u32：按钮图标颜色数值，0xargb格式；<br> .string：按钮图标地址。|
| NODE_TEXT_INPUT_TEXT_SELECTION | 单行文本设置文本选中并高亮的区域，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：选中文本的起始位置；<br> .value[1].i32：选中文本的终止位置；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：选中文本的起始位置；<br> .value[1].i32：选中文本的终止位置；|
| NODE_TEXT_INPUT_UNDERLINE_COLOR | 开启下划线时，支持配置下划线颜色。主题配置的默认下划线颜色为'0x33182431'。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：typing，必填，键入时下划线颜色，0xargb类型；<br> .value[1].u32：normal，必填，非特殊状态时下划线颜色，0xargb类型；<br> .value[2].u32：error，必填，错误时下划线颜色，0xargb类型；<br> .value[3].u32：disable，必填，禁用时下划线颜色，0xargb类型；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：typing，键入时下划线颜色，0xargb类型；<br> .value[1].u32：normal，非特殊状态时下划线颜色，0xargb类型；<br> .value[2].u32：error，错误时下划线颜色，0xargb类型；<br> .value[3].u32：disable，禁用时下划线颜色，0xargb类型；|
| NODE_TEXT_INPUT_ENABLE_AUTO_FILL | 设置是否启用自动填充。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 是否启用自动填充，默认值true。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 是否启用自动填充。 |
| NODE_TEXT_INPUT_CONTENT_TYPE | 自动填充类型。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 参数类型[ArkUI_TextInputContentType](capi-native-type-h.md#arkui_textinputcontenttype)。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 参数类型[ArkUI_TextInputContentType](capi-native-type-h.md#arkui_textinputcontenttype)。 |
| NODE_TEXT_INPUT_PASSWORD_RULES | 定义生成密码的规则。在触发自动填充时，所设置的密码规则会透传给密码保险箱，用于新密码的生成。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 定义生成密码的规则。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 定义生成密码的规则。|
| NODE_TEXT_INPUT_SELECT_ALL | 设置当初始状态，是否全选文本。不支持内联模式。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 是否全选文本，默认值：false。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 是否全选文本。|
| NODE_TEXT_INPUT_INPUT_FILTER | 通过正则表达式设置输入过滤器。匹配表达式的输入允许显示，不匹配的输入将被过滤。仅支持单个字符匹配，不支持字符串匹配。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 正则表达式。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 正则表达式。 |
| NODE_TEXT_INPUT_STYLE | 设置输入框为默认风格或内联输入风格。内联输入风格只支持InputType.Normal类型。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 参数类型[ArkUI_TextInputStyle](capi-native-type-h.md#arkui_textinputstyle)。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 参数类型[ArkUI_TextInputStyle](capi-native-type-h.md#arkui_textinputstyle)。 |
| NODE_TEXT_INPUT_CARET_OFFSET | 设置或获取光标所在位置信息。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> 设置输入光标的位置。.value[0].i32： 从字符串开始到光标所在位置的字符长度。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> 返回当前光标所在位置信息。在当前帧更新光标位置同时调用该接口，该接口不生效。value[0].i32：光标所在位置的索引值。<br> value[1].f32：光标相对输入框的x坐标位值。<br> value[2].f32：光标相对输入框的y坐标位值。 |
| NODE_TEXT_INPUT_CONTENT_RECT | 获取已编辑文本内容区域相对组件的位置和大小。属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> value[0].f32：水平方向横坐标。<br> value[1].f32：竖直方向纵坐标。<br> value[2].f32：内容宽度大小。<br> value[3].f32：内容高度大小。 |
| NODE_TEXT_INPUT_CONTENT_LINE_COUNT | 获取已编辑文本内容的行数。属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> value[0].i32：已编辑文本内容行数。 |
| NODE_TEXT_INPUT_SELECTION_MENU_HIDDEN | 设置长按、双击输入框或者右键输入框时，是否不弹出文本选择菜单，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 长按、双击输入框或者右键输入框时，是否不弹出文本选择菜单。默认值false。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 长按、双击输入框或者右键输入框时，是否不弹出文本选择菜单。 |
| NODE_TEXT_INPUT_BLUR_ON_SUBMIT | 设置输入框在submit状态下，触发回车键是否失焦。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：是否失焦。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：是否失焦。|
| NODE_TEXT_INPUT_CUSTOM_KEYBOARD | 设置自定义键盘。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .object：自定义键盘，参数类型[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。<br> .value[0]?.i32：设置自定义键盘是否支持避让功能，默认值false。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .object：自定义键盘，参数类型[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。<br> .value[0].i32：设置自定义键盘是否支持避让功能。 |
| NODE_TEXT_INPUT_WORD_BREAK | 文本断行规则属性，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32: 参数类型[ArkUI_WordBreak](capi-native-type-h.md#arkui_wordbreak)。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32: 参数类型[ArkUI_WordBreak](capi-native-type-h.md#arkui_wordbreak)。 |
| NODE_TEXT_INPUT_NUMBER_OF_LINES | 设置该属性后，通过该属性计算textInput组件的高度。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32: 设置numberOfLines的值。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32: 设置numberOfLines的值。 |
| NODE_TEXT_INPUT_LETTER_SPACING = 7032 | 设置该属性后，通过该属性调整textInput组件的字符间距。接口支持设置，重置以及获取该属性。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32: 设置letterSpacing的值，默认单位fp。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32: 获取letterSpacing的值，默认单位fp。<br>**起始版本：** 15   |
| NODE_TEXT_INPUT_ENABLE_PREVIEW_TEXT = 7033 | 设置textInput组件是否开启输入预上屏。接口支持设置，重置以及获取该属性。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32: 设置是否开启输入预上屏。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32: 获取是否开启输入预上屏。<br>**起始版本：** 15  |
| NODE_TEXT_INPUT_HALF_LEADING = 7034 | 设置文本将行间距平分至行的顶部与底部。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32: 设置文本是否将行间距平分至行的顶部与底部。默认值false。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32: 设置文本是否将行间距平分至行的顶部与底部。<br>**起始版本：** 18   |
| NODE_TEXT_INPUT_KEYBOARD_APPEARANCE = 7035 | 设置输入框拉起的键盘样式。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：键盘样式，参数类型[ArkUI_KeyboardAppearance](capi-native-type-h.md#arkui_keyboardappearance)。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：键盘样式，参数类型[ArkUI_KeyboardAppearance](capi-native-type-h.md#arkui_keyboardappearance)。<br>**起始版本：** 15  |
| NODE_TEXT_INPUT_ENABLE_FILL_ANIMATION = 7036 | 设置是否启用自动填充动效。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：是否启用自动填充动效。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：是否启用自动填充动效。<br>**起始版本：** 20  |
| NODE_TEXT_INPUT_SHOW_KEYBOARD_ON_FOCUS | 设置输入框获取焦点时是否弹出键盘，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 是否弹出键盘。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 是否弹出键盘。 |
| NODE_TEXT_INPUT_LINE_HEIGHT = 7037 | 设置输入框文本的高度，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：文本的高度的数字。默认值是自适应字体大小。设置为undefined时，文本的高度设置为5。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：文本的高度的数字。<br>**起始版本：** 20   |
| NODE_TEXT_AREA_PLACEHOLDER = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_AREA | 多行文本输入框的默认提示文本内容属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string：默认提示文本的内容。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string：默认提示文本的内容。 |
| NODE_TEXT_AREA_TEXT | 多行文本输入框的默认文本内容属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string：默认文本的内容。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string：默认文本的内容。 |
| NODE_TEXT_AREA_MAX_LENGTH | 输入框支持的最大文本数属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：最大文本数的数字。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：最大文本数的数字。|
| NODE_TEXT_AREA_PLACEHOLDER_COLOR | 无输入时默认提示文本的颜色属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：颜色数值，0xargb格式，形如 0xFFFF0000 表示红色。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：颜色数值，0xargb格式。 |
| NODE_TEXT_AREA_PLACEHOLDER_FONT | 无输入时默认提示文本的字体配置（包括大小、字重、样式、字体列表）属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0]?.f32：可选字体大小数值，默认值16.0，单位为fp；<br> .value[1]?.i32：可选字体样式[ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle)，默认值为ARKUI_FONT_STYLE_NORMAL；<br> .value[2]?.i32：可选字体粗细样式[ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight)，默认值为ARKUI_FONT_WEIGHT_NORMAL；<br> ?.string: 字体族内容，多个字体族之间使用逗号分隔，形如“字重；字体族1，字体族2”。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：字体大小数值，单位为fp；<br> .value[1].i32：字体样式[ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle)；<br> .value[2].i32：字体粗细样式[ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight)；<br> .string: 字体族内容，多个字体族之间使用逗号分隔。|
| NODE_TEXT_AREA_CARET_COLOR | 光标颜色属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：背景色数值，0xargb格式，形如 0xFFFF0000 表示红色。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：背景色数值，0xargb格式。|
| NODE_TEXT_AREA_EDITING | 控制多行文本输入框编辑态属性，支持属性设置。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：false表示退出编辑态，true表示维持现状。<br> 属性获取方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：false表示退出编辑态，true表示维持现状。 |
| NODE_TEXT_AREA_TYPE | 输入框的类型属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：输入框类型枚举[ArkUI_TextAreaType](capi-native-type-h.md#arkui_textareatype)，默认值为ARKUI_TEXTAREA_TYPE_NORMAL。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：输入框类型枚举[ArkUI_TextAreaType](capi-native-type-h.md#arkui_textareatype)。 |
| NODE_TEXT_AREA_SHOW_COUNTER | 设置输入的字符数超过阈值时是否显示计数器并设置计数器样式，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：是否开启计数器，值为true时为开启。<br> .value[1]?.f32：可输入字符数占最大字符限制的百分比值，超过此值时显示计数器，取值范围1-100，小数时向下取整。<br> .value[2]?.i32：输入字符超出限制时是否高亮边框。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：是否开启计数器。<br> .value[1].f32：可输入字符数占最大字符限制的百分比值，超过此值时显示计数器，取值范围1-100。<br> .value[2].i32：输入字符超出限制时是否高亮边框，默认高亮。|
| NODE_TEXT_AREA_SELECTION_MENU_HIDDEN | 设置长按、双击输入框或者右键输入框时，是否不弹出文本选择菜单，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 长按、双击输入框或者右键输入框时，是否不弹出文本选择菜单。默认值false。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 长按、双击输入框或者右键输入框时，是否不弹出文本选择菜单。|
| NODE_TEXT_AREA_BLUR_ON_SUBMIT | 设置多行输入框在submit状态下，触发回车键是否失焦。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：是否失焦。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：是否失焦。 |
| NODE_TEXT_AREA_INPUT_FILTER | 通过正则表达式设置输入过滤器。匹配表达式的输入允许显示，不匹配的输入将被过滤。仅支持单个字符匹配，不支持字符串匹配。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 正则表达式。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 正则表达式。 |
| NODE_TEXT_AREA_SELECTED_BACKGROUND_COLOR | 设置文本选中底板颜色，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：颜色数值，0xargb格式，形如 0xFFFF0000 表示红色。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：颜色数值，0xargb格式。 |
| NODE_TEXT_AREA_ENTER_KEY_TYPE | 设置输入法回车键类型，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：回车键类型枚举[ArkUI_EnterKeyType](capi-native-type-h.md#arkui_enterkeytype)，默认值为ARKUI_ENTER_KEY_TYPE_DONE。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：回车键类型枚举[ArkUI_EnterKeyType](capi-native-type-h.md#arkui_enterkeytype)。|
| NODE_TEXT_AREA_ENABLE_KEYBOARD_ON_FOCUS | 设置TextArea通过点击以外的方式获焦时，是否绑定输入法，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：false表示聚焦不拉起输入法，true表示拉起，默认值为true。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：0表示聚焦不拉起输入法，1表示拉起。 |
| NODE_TEXT_AREA_CARET_OFFSET | 设置或获取光标所在位置信息。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> 设置输入光标的位置。.value[0].i32： 从字符串开始到光标所在位置的字符长度。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> 返回当前光标所在位置信息。在当前帧更新光标位置同时调用该接口，该接口不生效。value[0].i32：光标所在位置的索引值。<br> value[1].f32：光标相对输入框的x坐标位值。<br> value[2].f32：光标相对输入框的y坐标位值。|
| NODE_TEXT_AREA_CONTENT_RECT | 获取已编辑文本内容区域相对组件的位置和大小。属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> value[0].f32：水平方向横坐标。<br> value[1].f32：竖直方向纵坐标。<br> value[2].f32：内容宽度大小。<br> value[3].f32：内容高度大小。 |
| NODE_TEXT_AREA_CONTENT_LINE_COUNT | 获取已编辑文本内容的行数。属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> value[0].i32：已编辑文本内容行数。 |
| NODE_TEXT_AREA_TEXT_SELECTION | 组件在获焦状态下，调用该接口设置文本选择区域并高亮显示，且只有在selectionStart小于selectionEnd时，文字才会被选取、高亮显示。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：选中文本的起始位置；<br> .value[1].i32：选中文本的终止位置；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：选中文本的起始位置；<br> .value[1].i32：选中文本的终止位置； |
| NODE_TEXT_AREA_ENABLE_AUTO_FILL | 设置是否启用自动填充。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 是否启用自动填充，默认值true。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 是否启用自动填充。 |
| NODE_TEXT_AREA_CONTENT_TYPE | 自动填充类型。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 参数类型[ArkUI_TextInputContentType](capi-native-type-h.md#arkui_textinputcontenttype)。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 参数类型[ArkUI_TextInputContentType](capi-native-type-h.md#arkui_textinputcontenttype)。|
| NODE_TEXT_AREA_NUMBER_OF_LINES | 设置该属性后，通过该属性计算textArea组件的高度。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32: 设置numberOfLines的值。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32: 设置numberOfLines的值。 |
| NODE_TEXT_AREA_LETTER_SPACING = 8023 | 设置该属性后，通过该属性调整textArea组件的字符间距。接口支持设置，重置以及获取该属性。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32: 设置letterSpacing的值，默认单位fp。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32: 获取letterSpacing的值，默认单位fp。<br>**起始版本：** 15  |
| NODE_TEXT_AREA_ENABLE_PREVIEW_TEXT = 8024 | 设置textArea组件是否开启输入预上屏。接口支持设置，重置以及获取该属性。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32: 设置是否开启输入预上屏。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32: 获取是否开启输入预上屏。<br>**起始版本：** 15  |
| NODE_TEXT_AREA_HALF_LEADING = 8025 | 设置文本将行间距平分至行的顶部与底部。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32: 设置文本是否将行间距平分至行的顶部与底部。默认值false。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32: 设置文本是否将行间距平分至行的顶部与底部。<br>**起始版本：** 18  |
| NODE_TEXT_AREA_KEYBOARD_APPEARANCE = 8026 | 设置输入框拉起的键盘样式。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：键盘样式，参数类型[ArkUI_KeyboardAppearance](capi-native-type-h.md#arkui_keyboardappearance)。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：键盘样式，参数类型[ArkUI_KeyboardAppearance](capi-native-type-h.md#arkui_keyboardappearance)。<br>**起始版本：** 15   |
| NODE_TEXT_AREA_MAX_LINES = 8027 | 设置输入框内联模式编辑态时文本可显示的最大行数，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：内联输入风格编辑态时文本可显示的最大行数。内联模式下，默认值是3，<br> 非内联模式下，默认值是+∞，不限制最大行数。设置为undefined时，最大行数设置为5。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：最大行数的数字。<br>**起始版本：** 20   |
| NODE_TEXT_AREA_LINE_SPACING = 8028 | 设置输入框文本的行间距，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：文本的行间距的数字。默认值是0。设置为undefined时，行间距设置为5。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：文本的行间距的数字。<br>**起始版本：** 20   |
| NODE_TEXT_AREA_MIN_LINES = 8029 | 设置节点的最小行数。支持属性设置、属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：最小行数的数字。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：最小行数的数字。<br>**起始版本：** 20  |
| NODE_TEXT_AREA_MAX_LINES_WITH_SCROLL = 8030 | 设置支持滚动时节点的最大行数。支持属性设置、属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：支持滚动时的最大行数的数字。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：支持滚动时的最大行数的数字。<br>**起始版本：** 20   |
| NODE_TEXT_AREA_SHOW_KEYBOARD_ON_FOCUS | 设置输入框获取焦点时是否弹出键盘，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 是否弹出键盘。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 是否弹出键盘。|
| NODE_TEXT_AREA_LINE_HEIGHT = 8031 | 设置输入框文本的高度，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：文本的高度的数字。默认值是自适应字体大小。设置为undefined时，文本的高度设置为5。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：文本的高度的数字。<br>**起始版本：** 20  |
| NODE_BUTTON_LABEL = MAX_NODE_SCOPE_NUM * ARKUI_NODE_BUTTON | button按钮的文本内容属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string：默认文本的内容。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string：默认文本的内容。 |
| NODE_BUTTON_TYPE | Button按钮的样式属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：设置Button按钮的样式，参数类型[ArkUI_ButtonType](capi-native-type-h.md#arkui_buttontype)，默认值为ARKUI_BUTTON_TYPE_CAPSULE。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：获取Button按钮的样式，参数类型[ArkUI_ButtonType](capi-native-type-h.md#arkui_buttontype)，默认值为ARKUI_BUTTON_TYPE_CAPSULE。  |
| NODE_BUTTON_MIN_FONT_SCALE | Button按钮的最小字体缩放倍数属性，支持属性设置，属性重置和属性获取。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32: 设置Button按钮的最小字体缩放倍数，默认单位fp。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32: 获取Button按钮的最小字体缩放倍数，默认单位fp。<br>**起始版本：** 18  |
| NODE_BUTTON_MAX_FONT_SCALE | Button按钮的最大字体缩放倍数属性，支持属性设置，属性重置和属性获取。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32: 设置Button按钮的最大字体缩放倍数，默认单位fp。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32: 获取Button按钮的最大字体缩放倍数，默认单位fp。<br>**起始版本：** 18   |
| NODE_PROGRESS_VALUE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_PROGRESS | 进度条的当前进度值属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：进度条当前值。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：进度条当前值。 |
| NODE_PROGRESS_TOTAL | 进度条的总长属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：进度条总长。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：进度条总长。 |
| NODE_PROGRESS_COLOR | 进度条显示进度值的颜色属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：颜色数值，0xargb格式，形如 0xFFFF0000 表示红色。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：颜色数值，0xargb格式。 |
| NODE_PROGRESS_TYPE | 进度条的类型属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：进度条类型枚举值[ArkUI_ProgressType](capi-native-type-h.md#arkui_progresstype)，默认值为ARKUI_PROGRESS_TYPE_LINEAR。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：进度条类型枚举值[ArkUI_ProgressType](capi-native-type-h.md#arkui_progresstype)。 |
| NODE_PROGRESS_LINEAR_STYLE | 线性进度条样式设置，支持属性设置，属性重置和属性获取接口，如果进度条类型不是线性样式则不生效。.object：使用[ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)对象设置组件样式。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .object：使用[ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)对象获取组件样式。<br>**起始版本：** 15 |
| NODE_CHECKBOX_SELECT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CHECKBOX | CheckBox多选框是否选中，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].i32：1表示选中，0表示不选中。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：1表示选中，0表示不选中。 |
| NODE_CHECKBOX_SELECT_COLOR | CheckBox多选框选中状态颜色，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].u32：多选框选中状态颜色, 类型为0xargb，如0xFF1122FF。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].u32：多选框选中状态颜色, 类型为0xargb，如0xFF1122FF。  |
| NODE_CHECKBOX_UNSELECT_COLOR | CheckBox多选框非选中状态边框颜色，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].u32：边框颜色, 类型为0xargb，如0xFF1122FF。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].u32：边框颜色, 类型为0xargb，如0xFF1122FF。 |
| NODE_CHECKBOX_MARK | CheckBox多选框内部图标样式，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].u32：边框颜色, 类型为0xargb，如0xFF1122FF；<br> .value[1]?.f32：可选，内部图标大小，单位vp；<br> .value[2]?.f32：可选，内部图标粗细，单位vp，默认值2。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].u32：边框颜色, 类型为0xargb，如0xFF1122FF；<br> .value[1].f32：内部图标大小，单位vp；<br> .value[2].f32：内部图标粗细，单位vp，默认值2。  |
| NODE_CHECKBOX_SHAPE | CheckBox组件形状, 支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].i32：组件形状，参数类型[ArkUI_CheckboxShape](capi-native-type-h.md#arkui_checkboxshape)。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：组件形状，参数类型[ArkUI_CheckboxShape](capi-native-type-h.md#arkui_checkboxshape)。   |
| NODE_CHECKBOX_NAME | 定义复选框的名称, 支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .string: 组件名称。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string: 组件名称。 <br> **起始版本：** 15  |
| NODE_CHECKBOX_GROUP | 定义复选框的组的名称, 支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .string: 组件名称。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string: 组件名称。 <br>**起始版本：** 15   |
| NODE_XCOMPONENT_ID = MAX_NODE_SCOPE_NUM * ARKUI_NODE_XCOMPONENT | XComponent组件ID属性，支持属性设置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string: ID的内容。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string: ID的内容。 |
| NODE_XCOMPONENT_TYPE | XComponent的类型，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：字体样式[ArkUI_XComponentType](capi-native-type-h.md#arkui_xcomponenttype)，默认值为ARKUI_XCOMPONENT_TYPE_SURFACE；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：字体样式[ArkUI_XComponentType](capi-native-type-h.md#arkui_xcomponenttype)。 |
| NODE_XCOMPONENT_SURFACE_SIZE | 设置XComponent的宽高，支持属性设置和获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：宽数值，单位为px；<br> .value[1].u32：高数值，单位为px；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：宽数值，单位为px；<br> .value[1].u32：高数值，单位为px； |
| NODE_XCOMPONENT_SURFACE_RECT | 设置XComponent组件持有Surface的显示区域，支持属性设置和获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32: Surface显示区域相对于XComponent组件左上角的x轴坐标, 单位为px。<br> .value[1].i32: Surface显示区域相对于XComponent组件左上角的y轴坐标, 单位为px。<br> .value[2].i32: Surface显示区域的宽度, 单位为px。<br> .value[3].i32: Surface显示区域的高度, 单位为px。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32: Surface显示区域相对于XComponent组件左上角的x轴坐标, 单位为px。<br> .value[1].i32: Surface显示区域相对于XComponent组件左上角的y轴坐标, 单位为px。<br> .value[2].i32: Surface显示区域的宽度, 单位为px。<br> .value[3].i32: Surface显示区域的高度, 单位为px。<br>**起始版本：** 18  |
| NODE_XCOMPONENT_ENABLE_ANALYZER | 设置XComponent组件是否支持图像分析，支持属性设置和获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> value[0].i32: 是否支持图像分析，1表示支持图像分析，0表示不支持图像分析。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> value[0].i32: 是否支持图像分析，1表示支持图像分析，0表示不支持图像分析。<br>**起始版本：** 18  |
| NODE_DATE_PICKER_LUNAR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_DATE_PICKER | 设置日期选择器组件的日期是否显示农历，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 是否显示农历，默认值false。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 是否显示农历。 |
| NODE_DATE_PICKER_START | 设置日期选择器组件选择器的起始日期，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 日期，默认值"1970-1-1"。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 日期。  <br>**起始版本：** 18|
| NODE_DATE_PICKER_END | 设置日期选择器组件选择器的结束日期，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 日期，默认值"2100-12-31"。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 日期。<br>**起始版本：** 18 |
| NODE_DATE_PICKER_SELECTED | 设置日期选择器组件选中项的日期，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 日期，默认值"2024-01-22"。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 日期。 |
| NODE_DATE_PICKER_DISAPPEAR_TEXT_STYLE | 设置日期选择器组件的所有选项中最上和最下两个选项的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 入参5个，格式为字符串，以 ';' 分割：<br>       入参1： 文本颜色，#argb类型。<br>       入参2： 文本大小，数字类型，单位fp。<br>       入参3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。<br>       入参4： 文本字体列表，使用 ',' 进行分割。<br>       入参5： 文本样式，字符串枚举("normal", "italic")。<br>       如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 参数5个，格式为字符串，以 ';' 分割：<br>       参数1： 文本颜色，#argb类型。<br>       参数2： 文本大小，数字类型，单位fp。<br>       参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。<br>       参数4： 文本字体列表，使用 ',' 进行分割。<br>       参数5： 文本样式，字符串枚举("normal", "italic")。<br>       如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。 |
| NODE_DATE_PICKER_TEXT_STYLE | 设置日期选择器组件的所有选项中除了最上、最下及选中项以外的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 入参5个，格式为字符串，以 ';' 分割：<br>       入参1： 文本颜色，#argb类型。<br>       入参2： 文本大小，数字类型，单位fp。<br>       入参3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。<br>       入参4： 文本字体列表，使用 ',' 进行分割。<br>       入参5： 文本样式，字符串枚举("normal", "italic")。<br>       如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 参数5个，格式为字符串，以 ';' 分割：<br>       参数1： 文本颜色，#argb类型。<br>       参数2： 文本大小，数字类型，单位fp。<br>       参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。<br>       参数4： 文本字体列表，使用 ',' 进行分割。<br>       参数5： 文本样式，字符串枚举("normal", "italic")。<br>       如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。 |
| NODE_DATE_PICKER_SELECTED_TEXT_STYLE | 设置日期选择器组件的选中项的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 入参5个，格式为字符串，以 ';' 分割：<br>       入参1： 文本颜色，#argb类型。<br>       入参2： 文本大小，数字类型，单位fp。<br>       入参3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。<br>       入参4： 文本字体列表，使用 ',' 进行分割。<br>       入参5： 文本样式，字符串枚举("normal", "italic")。<br>       如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 参数5个，格式为字符串，以 ';' 分割：<br>       参数1： 文本颜色，#argb类型。<br>       参数2： 文本大小，数字类型，单位fp。<br>       参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。<br>       参数4： 文本字体列表，使用 ',' 进行分割。<br>       参数5： 文本样式，字符串枚举("normal", "italic")。<br>       如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。 |
| NODE_DATE_PICKER_MODE = 13007 | 设置要显示的日期选项列。DatePicker显示不同样式的日期列，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)，格式：<br> .value[0].i32：显示的日期列类型。参数类型[ArkUI_DatePickerMode](capi-native-type-h.md#arkui_datepickermode)。\ n属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：显示的日期列类型。参数类型[ArkUI_DatePickerMode](capi-native-type-h.md#arkui_datepickermode)。<br>**起始版本：** 18  |
| NODE_DATE_PICKER_ENABLE_HAPTIC_FEEDBACK = 13008 | 设置是否开启触控反馈。支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：是否开启触控反馈。默认值：true，true表示开启触控反馈，false则表示不开启触控反馈。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> value[0].f32：是否开启触控反馈。 <br> **起始版本：** 18   |
| NODE_DATE_PICKER_CAN_LOOP = 13009 | Picker组件可循环滚动属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：false表示不可循环，true表示可循环。默认值：true，设置异常值时使用默认值。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> value[0].i32：0表示不可循环，1表示可循环。<br> 说明：可循环情况下，年份随着月份的循环滚动进行联动加减，月份随着日的循环滚动进行联动加减。<br> 不可循环情况下，年/月/日到达本列的顶部或底部时，无法再进行滚动，年/月/日之间也无法再联动加减。<br>     **起始版本：** 20  |
| NODE_DATE_PICKER_CAN_LOOP = 13009 | 设置时间选择组件选中项的时间，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 时间，默认值当前系统时间。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 时间。  |
| NODE_TIME_PICKER_USE_MILITARY_TIME | 设置时间选择组件展示时间是否为24小时制，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 是否为24小时制，默认值false。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 是否为24小时制。|
| NODE_TIME_PICKER_DISAPPEAR_TEXT_STYLE | 设置时间选择组件所有选项中最上和最下两个选项的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 入参5个，格式为字符串，以 ';' 分割：<br>       入参1： 文本颜色，#argb类型。<br>       入参2： 文本大小，数字类型，单位fp。<br>       入参3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。<br>       入参4： 文本字体列表，使用 ',' 进行分割。<br>       入参5： 文本样式，字符串枚举("normal", "italic")。<br>       如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 参数5个，格式为字符串，以 ';' 分割：<br>       参数1： 文本颜色，#argb类型。<br>       参数2： 文本大小，数字类型，单位fp。<br>       参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。<br>       参数4： 文本字体列表，使用 ',' 进行分割。<br>       参数5： 文本样式，字符串枚举("normal", "italic")。<br>       如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。|
| NODE_TIME_PICKER_TEXT_STYLE | 设置时间选择组件所有选项中除了最上、最下及选中项以外的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 入参5个，格式为字符串，以 ';' 分割：<br>       入参1： 文本颜色，#argb类型。<br>       入参2： 文本大小，数字类型，单位fp。<br>       入参3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。<br>       入参4： 文本字体列表，使用 ',' 进行分割。<br>       入参5： 文本样式，字符串枚举("normal", "italic")。<br>       如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 参数5个，格式为字符串，以 ';' 分割：<br>       参数1： 文本颜色，#argb类型。<br>       参数2： 文本大小，数字类型，单位fp。<br>       参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。<br>       参数4： 文本字体列表，使用 ',' 进行分割。<br>       参数5： 文本样式，字符串枚举("normal", "italic")。<br>       如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。 |
| NODE_TIME_PICKER_SELECTED_TEXT_STYLE | 设置时间选择组件选中项的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 入参5个，格式为字符串，以 ';' 分割：<br>       入参1： 文本颜色，#argb类型。<br>       入参2： 文本大小，数字类型，单位fp。<br>       入参3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。<br>       入参4： 文本字体列表，使用 ',' 进行分割。<br>       入参5： 文本样式，字符串枚举("normal", "italic")。<br>       如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 参数5个，格式为字符串，以 ';' 分割：<br>       参数1： 文本颜色，#argb类型。<br>       参数2： 文本大小，数字类型，单位fp。<br>       参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。<br>       参数4： 文本字体列表，使用 ',' 进行分割。<br>       参数5： 文本样式，字符串枚举("normal", "italic")。<br>       如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。 |
| NODE_TIME_PICKER_START = 14005 | 设置时间选择器组件的起始时间，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数 [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) 参数格式：<br> .string: 时间。 默认值："00:00:00"。<br> 属性获取方法返回值 [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) 参数格式：<br> .string: 时间。 默认值："00:00:00"。<br>**起始版本：** 18  |
| NODE_TIME_PICKER_END = 14006 | 设置时间选择器组件的结束日期，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数 [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) 参数格式：<br> .string: 时间。默认值："23:59:59"。<br> 属性获取方法返回值 [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) 参数格式：<br> .string: 时间。默认值："23:59:59"。<br>**起始版本：** 18  |
| NODE_TIME_PICKER_ENABLE_CASCADE = 14007 | 在设置12小时制时，上午和下午的标识会根据小时数自动切换，支持属性设置、重置和获取。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 在12小时制时，设置上午和下午的标识是否会根据小时数自动切换，默认值false。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 在12小时制时，设置上午和下午的标识是否会根据小时数自动切换。<br>**起始版本：** 18  |
| NODE_TEXT_PICKER_OPTION_RANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_PICKER | 设置滑动选择文本选择器的选择列表，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：使用的选择器类型[ArkUI_TextPickerRangeType](capi-native-type-h.md#arkui_textpickerrangetype)，默认值为ARKUI_TEXTPICKER_RANGETYPE_SINGLE；<br> ?.string：针对不同选择器类型有如下输入范式：<br> 1：单列选择器，入参格式为用分号分隔的一组字符串；<br> 2：多列选择器，支持多对纯文本字符串对，多对之间使用分号分隔，每对内部使用逗号分隔；<br> ?.object：针对不同选择器类型有如下输入范式：<br> 1：单列支持图片的选择器，输入结构体为[ARKUI_TextPickerRangeContent](capi-arkui-nativemodule-arkui-textpickerrangecontent.md)；<br> 2：多列联动选择器，输入结构体为[ARKUI_TextPickerCascadeRangeContent](capi-arkui-nativemodule-arkui-textpickercascaderangecontent.md)；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：使用的选择器类型[ArkUI_TextPickerRangeType](capi-native-type-h.md#arkui_textpickerrangetype)；<br> ?.string：针对不同选择器类型有如下输出范式：<br> 1：单列选择器，输出格式为用分号分隔的一组字符串；<br> 2：多列选择器，输出多对纯文本字符串对，多对之间使用分号分隔，每对内部使用逗号分隔；<br> ?.object：针对不同选择器类型有如下输出范式：<br> 1：单列支持图片的选择器，输出结构体为[ARKUI_TextPickerRangeContent](capi-arkui-nativemodule-arkui-textpickerrangecontent.md)；<br> 2：多列联动选择器，输出结构体为[ARKUI_TextPickerCascadeRangeContent](capi-arkui-nativemodule-arkui-textpickercascaderangecontent.md)； |
| NODE_TEXT_PICKER_OPTION_SELECTED | 设置滑动选择文本内容的组件默认选中项在数组中的索引值，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：索引值，如存在多个索引值则逐个添加。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：索引值，如存在多个索引值则逐个添加； |
| NODE_TEXT_PICKER_OPTION_VALUE | 设置滑动选择文本内容的组件默认选中项的值，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string：选中项的值，如存在多个值则逐个添加，用分号分隔。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string：选中项的值，如存在多个值则逐个添加，用分号分隔； |
| NODE_TEXT_PICKER_DISAPPEAR_TEXT_STYLE | 设置滑动选择文本内容的组件所有选项中最上和最下两个选项的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 入参5个，格式为字符串，以 ';' 分割：<br>       入参1： 文本颜色，#argb类型<br>       入参2： 文本大小，数字类型，单位fp<br>       入参3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")<br>       入参4： 文本字体列表，使用 ',' 进行分割<br>       入参5： 文本样式，字符串枚举("normal", "italic")<br>       如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 参数5个，格式为字符串，以 ';' 分割：<br>       参数1： 文本颜色，#argb类型<br>       参数2： 文本大小，数字类型，单位fp<br>       参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")<br>       参数4： 文本字体列表，使用 ',' 进行分割<br>       参数5： 文本样式，字符串枚举("normal", "italic")<br>       如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。 |
| NODE_TEXT_PICKER_TEXT_STYLE | 设置滑动选择文本内容的组件所有选项中除了最上、最下及选中项以外的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 入参5个，格式为字符串，以 ';' 分割：<br>       入参1： 文本颜色，#argb类型。<br>       入参2： 文本大小，数字类型，单位fp。<br>       入参3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。<br>       入参4： 文本字体列表，使用 ',' 进行分割。<br>       入参5： 文本样式，字符串枚举("normal", "italic")。<br>       如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 参数5个，格式为字符串，以 ';' 分割：<br>       参数1： 文本颜色，#argb类型。<br>       参数2： 文本大小，数字类型，单位fp。<br>       参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。<br>       参数4： 文本字体列表，使用 ',' 进行分割。<br>       参数5： 文本样式，字符串枚举("normal", "italic")。<br>       如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。 |
| NODE_TEXT_PICKER_SELECTED_TEXT_STYLE | 设置滑动选择文本内容的组件选中项的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 入参5个，格式为字符串，以 ';' 分割：<br>       入参1： 文本颜色，#argb类型；<br>       入参2： 文本大小，数字类型，单位fp；<br>       入参3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")；<br>       入参4： 文本字体列表，使用 ',' 进行分割；<br>       入参5： 文本样式，字符串枚举("normal", "italic")；<br>       如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .string： 参数5个，格式为字符串，以 ';' 分割：<br>       参数1： 文本颜色，#argb类型；<br>       参数2： 文本大小，数字类型，单位fp；<br>       参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")；<br>       参数4： 文本字体列表，使用 ',' 进行分割；<br>       参数5： 文本样式，字符串枚举("normal", "italic")；<br>       如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。  |
| NODE_TEXT_PICKER_SELECTED_INDEX | 设置滑动选择文本内容的组件默认选中项在数组中的索引值，支持属性设置，属性重置和属性获取接口。[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数类型：<br> .value[0...].i32：默认选中项在数组中的索引值数组。  |
| NODE_TEXT_PICKER_CAN_LOOP | Picker组件可循环滚动属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：false表示不可循环，true表示可循环。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> value[0].i32：0表示不可循环，1表示可循环。 |
| NODE_TEXT_PICKER_DEFAULT_PICKER_ITEM_HEIGHT | Picker各选择项的高度属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：子项高度属性，单位为vp。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> value[0].f32：子项高度属性，单位为vp。  |
| NODE_TEXT_PICKER_ENABLE_HAPTIC_FEEDBACK = 15010 | 设置是否开启触控反馈。支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：是否开启触控反馈。默认值：true，true表示开启触控反馈，false则表示不开启触控反馈。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> value[0].f32：是否开启触控反馈。 <br> **起始版本：** 18   |
| NODE_TEXT_PICKER_SELECTED_BACKGROUND_STYLE = 15011 | 设置选中项的背景颜色和边框圆角。支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：背景颜色，采用 0xARGB 格式，例如，<b>0xFF1122FF</b>。 <br> 1：.value[1].f32：四个角的圆角半径，单位为VP。 <br> 2：.value[1].f32：左上角的圆角半径，单位为VP。 <br> .value[2].f32：右上角的圆角半径，单位为VP。 <br> .value[3].f32：左下角的圆角半径，单位为VP。 <br> .value[4].f32：右下角的圆角半径，单位为VP。 <br> 默认值：背景颜色：0x0C182431；圆角半径：24.0。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32：背景颜色，采用 0xARGB 格式，例如，<b>0xFF1122FF</b>。 <br> .value[1].f32：左上角的圆角半径，单位为VP。 <br> .value[2].f32：右上角的圆角半径，单位为VP。 <br> .value[3].f32：左下角的圆角半径，单位为VP。 <br> .value[4].f32：右下角的圆角半径，单位为VP。 <br>**起始版本：** 20  |
| NODE_CALENDAR_PICKER_HINT_RADIUS = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CALENDAR_PICKER | 设置日历选中态底板圆角半径的参数，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32： 日历选中态底板圆角半径，取值范围[0,+∞)，其中取值为0表示底板样式为直角矩形；取值范围为(0, 16)时，底板样式为圆角矩形；取值范围为[16,+∞)时，底板样式为圆形。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32： 日历选中态底板圆角半径，取值范围[0,+∞)，其中取值为0表示底板样式为直角矩形；取值范围为(0, 16)时，底板样式为圆角矩形；取值范围为[16,+∞)时，底板样式为圆形。 |
| NODE_CALENDAR_PICKER_SELECTED_DATE | 设置日历选择选中日期的参数，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32： 选中的年。<br> .value[1].u32： 选中的月。<br> .value[2].u32： 选中的日。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32： 选中的年。<br> .value[1].u32： 选中的月。<br> .value[2].u32： 选中的日。 |
| NODE_CALENDAR_PICKER_EDGE_ALIGNMENT | 设置日历选择器与入口组件的对齐方式，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 对齐方式类型，参数类型[ArkUI_CalendarAlignment](capi-native-type-h.md#arkui_calendaralignment)。<br> .value[1]?.f32： 按照对齐方式对齐后，选择器相对入口组件的x轴方向相对偏移。<br> .value[2]?.f32： 按照对齐方式对齐后，选择器相对入口组件的y轴方向相对偏移。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 对齐方式类型，参数类型[ArkUI_CalendarAlignment](capi-native-type-h.md#arkui_calendaralignment)。<br> .value[1].f32： 按照对齐方式对齐后，选择器相对入口组件的x轴方向相对偏移。<br> .value[2].f32： 按照对齐方式对齐后，选择器相对入口组件的y轴方向相对偏移。 |
| NODE_CALENDAR_PICKER_TEXT_STYLE | 设置日历选择器入口区的文本颜色、字号、字体粗细。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0]?.u32： 入口区的文本颜色。<br> .value[1]?.f32： 入口区的文本字号，单位为fp。<br> .value[2]?.i32： 入口区的文本字体粗细，参数类型[ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight)。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32： 入口区的文本颜色。<br> .value[1].f32： 入口区的文本字号，单位为fp。<br> .value[2].i32： 入口区的文本字体粗细，参数类型[ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight)。 |
| NODE_CALENDAR_PICKER_START = 16004 | 设置日历选择器的开始日期，支持属性设置，属性重置和属性获取接口。设置属性时的参数格式为[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)：<br> .string: 日期。值的格式如 "1970-1-1"。 <br> 获取属性时的返回值格式为[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)：<br> .string: 日期。 <br>**起始版本：** 18  |
| NODE_CALENDAR_PICKER_END = 16005 | 设置日历选择器的结束日期，支持属性设置，属性重置和属性获取接口。设置属性时的参数格式为[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)：<br> .string: 日期。值的格式如 "2100-12-31"。 <br> 获取属性时的返回值格式为[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)：<br> .string: 日期。 <br>**起始版本：** 18  |
| NODE_CALENDAR_PICKER_DISABLED_DATE_RANGE = 16006 | 设置日历选择器的禁用日期区间，支持属性设置，属性重置和属性获取接口。设置属性时的参数格式为[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)：<br> .string: 禁用日期区间字符串。禁用日期区间："第一个区间开始日期,第一个区间结束日期,第二个区间开始日期,第二个区间结束日期,...,第n个区间开始日期,第n个区间结束日期"。<br> 设置的禁用日期区间格式："1910-01-01,1910-12-31,2020-01-01,2020-12-31"。<br> 获取属性时的返回值格式为[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)：<br> .string: 禁用日期区间字符串。<br>**起始版本：** 19  |
| NODE_CALENDAR_PICKER_MARK_TODAY = 16007 | 设置日历选择器在系统当前日期时，是否保持高亮显示，支持属性设置，属性重置和属性获取接口。设置属性时的参数格式为[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)：<br> value[0].i32: 日历选择器在系统当前日期时，是否保持高亮显示。默认值：false。<br> 获取属性时的返回值格式为[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)：<br> value[0].i32: 日历选择器在系统当前日期时，是否保持高亮显示。<br>**起始版本：** 19   |
| NODE_SLIDER_BLOCK_COLOR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SLIDER | Slider滑块的颜色，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].u32：滑块的颜色, 类型为0xargb，如0xFF1122FF。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].u32：滑块的颜色, 类型为0xargb，如0xFF1122FF。 |
| NODE_SLIDER_TRACK_COLOR | Slider滑轨的背景颜色，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].u32：背景颜色, 类型为0xargb，如0xFF1122FF。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].u32：背景颜色, 类型为0xargb，如0xFF1122FF。   |
| NODE_SLIDER_SELECTED_COLOR | Slider滑轨的已滑动部分颜色，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].u32：已滑动部分颜色, 类型为0xargb，如0xFF1122FF。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].u32：已滑动部分颜色, 类型为0xargb，如0xFF1122FF。  |
| NODE_SLIDER_SHOW_STEPS | 设置是否显示步长刻度值，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].i32：是否显示步长刻度值，1表示显示，0表示不显示，默认值为0。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：是否显示步长刻度值，1表示显示，0表示不显示，默认值为0。 |
| NODE_SLIDER_BLOCK_STYLE | Slider滑块形状参数，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].i32：形状参数。参数类型[ArkUI_SliderBlockStyle](capi-native-type-h.md#arkui_sliderblockstyle)。<br> .string? 可选值，根据形状参数而定。<br> ARKUI_SLIDER_BLOCK_STYLE_IMAGE: 滑块图片资源。如/pages/common/icon.png。<br> ARKUI_SLIDER_BLOCK_STYLE_SHAPE: 滑块使用的自定义形状。<br> 共有5种类型： <br> 1.rect类型： <br> .value[1].i32：裁剪类型，参数类型[ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype)，ARKUI_SHAPE_TYPE_RECTANGLE； <br> .value[2].f32：矩形宽度； <br> .value[3].f32：矩形高度； <br> .value[4].f32：矩形圆角宽度； <br> .value[5].f32：矩形圆角高度； <br> 2.circle类型： <br> .value[1].i32：裁剪类型，参数类型[ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype)，ARKUI_SHAPE_TYPE_CIRCLE； <br> .value[2].f32：圆形宽度； <br> .value[3].f32：圆形高度； <br> 3.ellipse类型： <br> .value[1].i32：裁剪类型，参数类型[ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype)，ARKUI_SHAPE_TYPE_ELLIPSE； <br> .value[2].f32：椭圆形宽度； <br> .value[3].f32：椭圆形高度； <br> 4.path类型： <br> .value[1].i32：裁剪类型，参数类型[ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype)，ARKUI_SHAPE_TYPE_PATH； <br> .value[2].f32：路径宽度； <br> .value[3].f32：路径高度； <br> .string：路径绘制的命令字符串； <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：形状参数。参数类型[ArkUI_SliderBlockStyle](capi-native-type-h.md#arkui_sliderblockstyle)。<br> .string? 可选值，根据形状参数而定。<br> ARKUI_SLIDER_BLOCK_STYLE_IMAGE: 滑块图片资源。如/pages/common/icon.png。<br> ARKUI_SLIDER_BLOCK_STYLE_SHAPE: 滑块使用的自定义形状。<br> 共有5种类型： <br> 1.rect类型： <br> .value[1].i32：裁剪类型，参数类型[ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype)，ARKUI_SHAPE_TYPE_RECTANGLE； <br> .value[2].f32：矩形宽度； <br> .value[3].f32：矩形高度； <br> .value[4].f32：矩形圆角宽度； <br> .value[5].f32：矩形圆角高度； <br> 2.circle类型： <br> .value[1].i32：裁剪类型，参数类型[ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype)，ARKUI_SHAPE_TYPE_CIRCLE； <br> .value[2].f32：圆形宽度； <br> .value[3].f32：圆形高度； <br> 3.ellipse类型： <br> .value[1].i32：裁剪类型，参数类型[ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype)，ARKUI_SHAPE_TYPE_ELLIPSE； <br> .value[2].f32：椭圆形宽度； <br> .value[3].f32：椭圆形高度； <br> 4.path类型： <br> .value[1].i32：裁剪类型，参数类型[ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype)，ARKUI_SHAPE_TYPE_PATH； <br> .value[2].f32：路径宽度； <br> .value[3].f32：路径高度； <br> .string：路径绘制的命令字符串；  |
| NODE_SLIDER_VALUE | slider进度值，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].f32：进度值。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：进度值。  |
| NODE_SLIDER_MIN_VALUE | slider最小值，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].f32：进度值的最小值。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：进度值的最小值。  |
| NODE_SLIDER_MAX_VALUE | slider最大值，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].f32：进度值的最大值。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：进度值的最大值。  |
| NODE_SLIDER_STEP | Slider滑动步长，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].f32：滑动步长，取值范围：[0.01, 100]。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：滑动步长，取值范围：[0.01, 100]。 |
| NODE_SLIDER_DIRECTION | Slider滑动条滑动方向，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].i32：显示样式，参数类型[ArkUI_SliderDirection](capi-native-type-h.md#arkui_sliderdirection)。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：显示样式，参数类型[ArkUI_SliderDirection](capi-native-type-h.md#arkui_sliderdirection)。 |
| NODE_SLIDER_REVERSE | Slider滑动条取值范围是否反向，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].i32：是否反向，1表示反向，0表示不反向。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：是否反向，1表示反向，0表示不反向。  |
| NODE_SLIDER_STYLE | Slider的滑块与滑轨显示样式，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].i32：显示样式，参数类型[ArkUI_SliderStyle](capi-native-type-h.md#arkui_sliderstyle)。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：显示样式，参数类型[ArkUI_SliderStyle](capi-native-type-h.md#arkui_sliderstyle)。 |
| NODE_SLIDER_TRACK_THICKNESS | Slider滑块的滑轨粗细属性，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].f32：滑轨的粗细，单位为vp；当参数NODE_SLIDER_STYLE的值设置为ARKUI_SLIDER_STYLE_OUT_SET时为4.0vp，设置为ARKUI_SLIDER_STYLE_IN_SET时为20.0vp <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：滑轨的粗细，单位为vp；  |
| NODE_SLIDER_ENABLE_HAPTIC_FEEDBACK = 17013 | 设置是否开启触控反馈。支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：是否开启触控反馈。默认值：true，true表示开启触控反馈，false则表示不开启触控反馈。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> value[0].f32：是否开启触控反馈。 <br> 开启触控反馈时，需要在工程的module.json5的requestPermissions字段中增加"name": "ohos.permission.VIBRATE"，开启振动权限。<br>**起始版本：** 18   |
| NODE_SLIDER_PREFIX | 在Slider组件的前端设置自定义组件。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .object: 参数类型 [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。前缀组件将放置在Slider组件的起始位置，通常在LTR布局的左侧。<br>**起始版本：** 20   |
| NODE_SLIDER_SUFFIX | 在Slider组件的后端设置自定义组件。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .object: 参数类型 [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。后缀组件将放置在Slider组件的尾侧位置，通常在LTR布局的右侧。<br>**起始版本：** 20    |
| NODE_RADIO_CHECKED = MAX_NODE_SCOPE_NUM * ARKUI_NODE_RADIO | 设置单选框的选中状态，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].i32：单选框的选中状态，默认值false。属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：单选框的选中状态。 |
| NODE_RADIO_STYLE | 设置单选框选中状态和非选中状态的样式，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0]?.u32：开启状态底板颜色, 类型为0xargb，默认值为0xFF007DFF。<br> .value[1]?.u32：关闭状态描边颜色, 类型为0xargb，默认值为0xFF182431。<br> .value[2]?.u32：开启状态内部圆饼颜色, 类型为0xargb，默认值为0xFFFFFFFF。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].u32：开启状态底板颜色, 类型为0xargb，默认值为0xFF007DFF。<br> .value[1].u32：关闭状态描边颜色, 类型为0xargb，默认值为0xFF182431。<br> .value[2].u32：开启状态内部圆饼颜色, 类型为0xargb，默认值为0xFFFFFFF。 |
| NODE_RADIO_VALUE | 设置当前单选框的值，支持属性设置、重置和获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .string: 单选框的值.<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .string: 单选框的值. |
| NODE_RADIO_GROUP | 设置当前单选框的所属群组名称，相同group的Radio只能有一个被选中，支持属性设置、重置和获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .string: 当前单选框的所属群组名称.<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .string: 当前单选框的所属群组名称. |
| NODE_CHECKBOX_GROUP_NAME = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CHECKBOX_GROUP | 定义复选框组的名称, 支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .string: 组件名称。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .string: 组件名称。 <br>**起始版本：** 15  |
| NODE_CHECKBOX_GROUP_SELECT_ALL | CheckBoxGroup多选框组是否全选, 支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].i32: 是否设置全选1表示选中，0表示不选中。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32: 1表示选中，0表示不选中。<br>**起始版本：** 15    |
| NODE_CHECKBOX_GROUP_SELECTED_COLOR | CheckBoxGroup多选框选中状态颜色, 支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].u32: CheckBoxGroup多选框选中状态颜色, 0xARGB格式。例如0xFF1122FF。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].u32:  CheckBoxGroup多选框选中状态颜色, 0xARGB格式。例如0xFF1122FF。<br>**起始版本：** 15   |
| NODE_CHECKBOX_GROUP_UNSELECTED_COLOR | CheckBoxGroup多选框未选中边框颜色, 支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].u32: 边框颜色, 类型为0xargb，如0xFF1122FF。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].u32: 边框颜色, 类型为0xargb，如0xFF1122FF。<br>**起始版本：** 15   |
| NODE_CHECKBOX_GROUP_MARK | CheckBoxGroup多选框内部图标样式, 支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].u32: 边框颜色, 类型为0xargb，如0xFF1122FF；<br> .value[1]?.f32: 可选，内部图标大小，单位vp；<br> .value[2]?.f32: 可选，内部图标粗细，单位vp，默认值2。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].u32: 边框颜色, 类型为0xargb，如0xFF1122FF；<br> .value[1]?.f32: 可选，内部图标大小，单位vp；<br> .value[2]?.f32: 可选，内部图标粗细，单位vp，默认值2。<br>**起始版本：** 15  |
| NODE_CHECKBOX_GROUP_SHAPE | CheckBoxGroup组件形状, 支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].i32: 组件形状，参数类型[ArkUI_CheckboxShape](capi-native-type-h.md#arkui_checkboxshape)。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32: 组件形状，参数类型[ArkUI_CheckboxShape](capi-native-type-h.md#arkui_checkboxshape)。<br>**起始版本：** 15  |
| NODE_STACK_ALIGN_CONTENT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_STACK | 设置子组件在容器内的对齐方式，支持属性设置，属性重置和属性获取接口。该属性与通用属性NODE_ALIGNMENT同时设置时，后设置的属性生效。<br> <br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 对齐方式，数据类型[ArkUI_Alignment](capi-native-type-h.md#arkui_alignment)，默认值ARKUI_ALIGNMENT_CENTER。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 对齐方式，数据类型[ArkUI_Alignment](capi-native-type-h.md#arkui_alignment)。 |
| NODE_SCROLL_BAR_DISPLAY_MODE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SCROLL | 设置滚动条状态，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 滚动条状态，数据类型[ArkUI_ScrollBarDisplayMode](capi-native-type-h.md#arkui_scrollbardisplaymode)，默认值ARKUI_SCROLL_BAR_DISPLAY_MODE_AUTO。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 滚动条状态，数据类型[ArkUI_ScrollBarDisplayMode](capi-native-type-h.md#arkui_scrollbardisplaymode)。 |
| NODE_SCROLL_BAR_WIDTH | 设置滚动条的宽度，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32： 滚动条宽度，单位vp，默认值4。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32： 滚动条宽度，单位vp。  |
| NODE_SCROLL_BAR_COLOR | 设置滚动条的颜色，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .data[0].u32： 滚动条颜色，0xargb类型。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .data[0].u32： 滚动条颜色，0xargb类型。 |
| NODE_SCROLL_SCROLL_DIRECTION | 设置滚动方向，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：滚动方向，数据类型[ArkUI_ScrollDirection](capi-native-type-h.md#arkui_scrolldirection)，默认值ARKUI_SCROLL_DIRECTION_VERTICAL。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：滚动方向，数据类型[ArkUI_ScrollDirection](capi-native-type-h.md#arkui_scrolldirection)。 |
| NODE_SCROLL_EDGE_EFFECT | 设置边缘滑动效果，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 边缘滑动效果，参数类型[ArkUI_EdgeEffect](capi-native-type-h.md#arkui_edgeeffect)，默认值ARKUI_EDGE_EFFECT_NONE；<br> .value[1]?.i32： 可选值，组件内容大小小于组件自身时，设置是否开启滑动效果，开启为1，关闭为0，List/Grid/WaterFlow组件默认值为0，Scroll组件默认值为1；<br> .value[2]?.i32： 边缘效果生效的方向，参数类型[ArkUI_EffectEdge](capi-native-type-h.md#arkui_effectedge)，默认值ARKUI_EFFECT_EDGE_START  \| ARKUI_EFFECT_EDGE_END。<br> 该参数从API version 18开始支持。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 边缘滑动效果，参数类型[ArkUI_EdgeEffect](capi-native-type-h.md#arkui_edgeeffect)；<br> .value[1].i32： 组件内容大小小于组件自身时，设置是否开启滑动效果，开启为1，关闭为0；<br> .value[2].i32： 边缘效果生效的方向，参数类型[ArkUI_EffectEdge](capi-native-type-h.md#arkui_effectedge)。该参数从API version 18开始支持。 |
| NODE_SCROLL_ENABLE_SCROLL_INTERACTION | 设置是否支持滚动手势，当设置为false时，无法通过手指或者鼠标滚动，但不影响控制器的滚动接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 是否支持滚动手势，默认值true。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 是否支持滚动手势。|
| NODE_SCROLL_FRICTION | 设置摩擦系数，手动划动滚动区域时生效，只对惯性滚动过程有影响，对惯性滚动过程中的链式效果有间接影响。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32： 摩擦系数，默认值：非可穿戴设备为0.6，可穿戴设备为0.9。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32： 摩擦系数。|
| NODE_SCROLL_SNAP | 设置Scroll组件的限位滚动模式，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： Scroll组件限位滚动时的对其方式，数据类型[ArkUI_ScrollSnapAlign](capi-native-type-h.md#arkui_scrollsnapalign)，默认值ARKUI_SCROLL_SNAP_ALIGN_NONE；<br> .value[1].i32： 在Scroll组件限位滚动模式下，该属性设置为false后，运行Scroll在开头和第一个限位点间自由滑动。默认值true，仅在限位点为多个时生效；<br> .value[2].i32： 在Scroll组件限位滚动模式下，该属性设置为false后，运行Scroll在最后一个限位点和末尾间自由滑动。默认值true，仅在限位点为多个时生效；<br> .value[3...].f32： Scroll组件限位滚动时的限位点，限位点即为Scroll组件能滑动停靠的偏移量。可以1个或多个。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： Scroll组件限位滚动时的对其方式，数据类型[ArkUI_ScrollSnapAlign](capi-native-type-h.md#arkui_scrollsnapalign)；<br> .value[1].i32： 在Scroll组件限位滚动模式下，该属性设置为false后，运行Scroll在开头和第一个限位点间自由滑动；<br> .value[2].i32： 在Scroll组件限位滚动模式下，该属性设置为false后，运行Scroll在最后一个限位点和末尾间自由滑动；<br> .value[3...].f32： Scroll组件限位滚动时的限位点，限位点即为Scroll组件能滑动停靠的偏移量。 |
| NODE_SCROLL_NESTED_SCROLL | Scroll嵌套滚动选项，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].i32：可滚动组件往末尾端滚动时的嵌套滚动，参数类型[ArkUI_ScrollNestedMode](capi-native-type-h.md#arkui_scrollnestedmode)。<br> .value[1].i32：可滚动组件往起始端滚动时的嵌套滚动，参数类型[ArkUI_ScrollNestedMode](capi-native-type-h.md#arkui_scrollnestedmode)。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：可滚动组件往末尾端滚动时的嵌套滚动，参数类型[ArkUI_ScrollNestedMode](capi-native-type-h.md#arkui_scrollnestedmode)。<br> .value[1].i32：可滚动组件往起始端滚动时的嵌套滚动，参数类型[ArkUI_ScrollNestedMode](capi-native-type-h.md#arkui_scrollnestedmode)。 |
| NODE_SCROLL_OFFSET | Scroll滑动到指定位置，支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].f32：水平滑动偏移，单位为vp。<br> .value[1].f32：垂直滑动偏移，单位为vp。<br> .value[2]?.i32：可选值，滚动时长，单位为毫秒。<br> .value[3]?.i32：可选值，滚动曲线，参数类型[ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve)。默认值为ARKUI_CURVE_EASE。<br> .value[4]?.i32：可选值，是否使能默认弹簧动效，默认值为0不使能。 <br> .value[5]?.i32：可选值，设置动画滚动到边界是否转换为越界回弹动画。 <br> .value[6]?.i32：可选值，设置滚动是否可以停留在越界位置。该参数从API version 20开始支持。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：水平滑动偏移，单位为vp。<br> .value[1].f32：垂直滑动偏移，单位为vp。 |
| NODE_SCROLL_EDGE | Scroll滚动到容器边缘，支持属性设置，属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].i32：容器边缘，参数类型[ArkUI_ScrollEdge](capi-native-type-h.md#arkui_scrolledge)。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：容器是否位于边缘，-1：表示未处于边缘，如果处于边缘状态参数类型[ArkUI_ScrollEdge](capi-native-type-h.md#arkui_scrolledge)。|
| NODE_SCROLL_ENABLE_PAGING | 设置是否支持滑动翻页，支持属性设置，属性重置和属性获取接口。如果同时设置了划动翻页enablePaging和限位滚动scrollSnap，则scrollSnap优先生效，enablePaging不生效。<br> <br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 是否支持划动翻页，默认值false。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： 是否支持划动翻页。 |
| NODE_SCROLL_PAGE | 滚动到下一页或者上一页。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32 是否向下翻页。0表示向下翻页，1表示向上翻页。<br> .value[1]?.i32 是否开启翻页动画效果。1有动画，0无动画。默认值：0。 |
| NODE_SCROLL_BY | 滑动指定距离。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：水平方向滚动距离，默认单位为vp; <br> .value[1].f32: 竖直方向滚动距离，默认单位为vp。  |
| NODE_SCROLL_FLING | 滚动类组件按传入的初始速度进行惯性滚动。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：惯性滚动的初始速度，默认单位为vp/s。值设置为0，视为异常值，本次滚动不生效。如果值为正数，则向下滚动；如果值为负数，则向上滚动。 <br>**起始版本：** 13  |
| NODE_SCROLL_FADING_EDGE | 设置滚动类组件边缘渐隐效果。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：是否使能边缘渐隐效果。0表示关闭边缘效果。1表示开启边缘效果。 <br> .value[1]?.f32：边缘渐隐效果长度。单位：vp，默认值：32。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：是否使能边缘渐隐效果。0表示关闭边缘效果。1表示开启边缘效果。 <br> .value[1].f32：边缘渐隐效果长度。单位：vp。 <br>**起始版本：** 14  |
| NODE_SCROLL_SIZE | 获取滚动类组件所有子组件全展开尺寸。属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：滚动类组件所有子组件全展开的宽度，默认单位为vp。<br> .value[1].f32：滚动类组件所有子组件全展开的高度，默认单位为vp。<br> 设置NODE_PADDING、NODE_MARGIN或NODE_BORDER_WIDTH后，NODE_PADDING、NODE_MARGIN或NODE_BORDER_WIDTH在单位vp转换成单位px时会进行像素取整，返回值根据取整后的值计算。<br>**起始版本：** 14  |
| NODE_SCROLL_CONTENT_START_OFFSET | 设置取滚动类组件内容起始端偏移量。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32： 内容起始端偏移量，单位vp；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32： 内容起始端偏移量，单位vp；<br>**起始版本：** 15  |
| NODE_SCROLL_CONTENT_END_OFFSET | 设置取滚动类组件内容末尾端偏移量。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32： 内容末尾端偏移量，单位vp；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32： 内容末尾端偏移量，单位vp；<br>**起始版本：** 15   |
| NODE_SCROLL_FLING_SPEED_LIMIT = 1002019 | 限制跟手滑动结束后，Fling动效开始时的最大初始速度。支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：Fling动效开始时的最大初始速度，单位：vp/s。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：Fling动效开始时的最大初始速度。 <br>**起始版本：** 18  |
| NODE_SCROLL_CLIP_CONTENT = 1002020 | 设置滚动容器的内容层裁剪区域。支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：内容裁剪模式，参数类型[ArkUI_ContentClipMode](capi-native-type-h.md#arkui_contentclipmode)。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：内容裁剪模式，参数类型[ArkUI_ContentClipMode](capi-native-type-h.md#arkui_contentclipmode)。 <br>**起始版本：** 18  |
| NODE_SCROLL_BACK_TO_TOP = 1002021 | 设置滚动容器是否在点击状态栏时回到顶部。支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：是否回到顶部，1表示回到顶部，0表示保持当前位置不变，默认值：API version 18之前：0。API version 18及以后：滚动方向是水平方向时为0，是垂直方向时为1。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：是否回到顶部。 <br>**起始版本：** 15 |
| NODE_SCROLL_BAR_MARGIN = 1002022 | 设置滚动条的边距，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：设置滚动条起始边距，默认值为0，单位：vp。 <br> .value[1].f32：设置滚动条末尾边距，默认值为0，单位：vp。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：滚动条起始边距，单位：vp。 <br> .value[1].f32：滚动条末尾边距，单位：vp。 <br>**起始版本：** 20  |
| NODE_SCROLL_MAX_ZOOM_SCALE = 1002023 | 设置滚动内容最大缩放比例。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：设置内容最大缩放比例。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：获取内容最大缩放比例。 <br>**起始版本：** 20  |
| NODE_SCROLL_MIN_ZOOM_SCALE = 1002024 | 设置滚动内容最小缩放比例。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：设置内容最小缩放比例。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：获取内容最小缩放比例。 <br>**起始版本：** 20 |
| NODE_SCROLL_ZOOM_SCALE = 1002025 | 设置滚动内容缩放比例。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：设置内容缩放比例。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：获取内容缩放比例。 <br>**起始版本：** 20  |
| NODE_SCROLL_ENABLE_BOUNCES_ZOOM = 1002026 | 设置是否支持过缩放回弹效果。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：是否支持过缩放回弹效果，0：不支持，1：支持。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：是否支持过缩放回弹效果，0：不支持，1：支持。 <br>**起始版本：** 20    |
| NODE_LIST_DIRECTION = MAX_NODE_SCOPE_NUM * ARKUI_NODE_LIST | 设置List组件排列方向。支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：List组件排列方向，数据类型[ArkUI_Axis](capi-native-type-h.md#arkui_axis)，默认值ARKUI_AXIS_VERTICAL。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：List组件排列方向，数据类型[ArkUI_Axis](capi-native-type-h.md#arkui_axis)。 |
| NODE_LIST_STICKY | 配合ListItemGroup组件使用，设置ListItemGroup中header和footer是否要吸顶或吸底，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：配合ListItemGroup组件使用，设置ListItemGroup中header和footer是否要吸顶或吸底。数据类型[ArkUI_StickyStyle](capi-native-type-h.md#arkui_stickystyle)，默认值ARKUI_STICKY_STYLE_NONE。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：配合ListItemGroup组件使用，设置ListItemGroup中header和footer是否要吸顶或吸底。数据类型[ArkUI_StickyStyle](capi-native-type-h.md#arkui_stickystyle)。 |
| NODE_LIST_SPACE | 设置列表项间距，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32： 子组件主轴方向的间隔。默认值0。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32： 子组件主轴方向的间隔。 |
| NODE_LIST_NODE_ADAPTER | list组件适配器，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .object：使用[ArkUI_NodeAdapter](capi-arkui-nativemodule-arkui-nodeadapter8h.md)对象作为适配器。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .object：返回值格式为[ArkUI_NodeAdapter](capi-arkui-nativemodule-arkui-nodeadapter8h.md)。|
| NODE_LIST_CACHED_COUNT | list组件Adapter缓存数量，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：配合List组件Adapter使用，设置adapter中的缓存数量<br> .value[1]?.i32：是否显示缓存节点，0：不显示，1：显示，默认值：0。该参数从API version 15开始支持。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：adapter中的缓存数量。<br> .value[1].i32：是否显示缓存节点，0：不显示，1：显示。该参数从API version 15开始支持。 |
| NODE_LIST_SCROLL_TO_INDEX | 滑动到指定index。开启smooth动效时，会对经过的所有item进行加载和布局计算，当大量加载item时会导致性能问题。<br> <br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：要滑动到的目标元素在当前容器中的索引值。<br> .value[1]?.i32：设置滑动到列表项在列表中的索引值时是否有动效，1表示有动效，0表示没有动效。默认值：0。<br> .value[2]?.i32：指定滑动到的元素与当前容器的对齐方式，参数类型[ArkUI_ScrollAlignment](capi-native-type-h.md#arkui_scrollalignment), 默认值：ARKUI_SCROLL_ALIGNMENT_START。<br> .value[3]?.i32：额外偏移量，默认值：0，单位：vp。该参数从API version 16开始支持。 |
| NODE_LIST_ALIGN_LIST_ITEM | 设置List交叉轴方向宽度大于ListItem交叉轴宽度 * lanes时，ListItem在List交叉轴方向的布局方式，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：交叉轴方向的布局方式。参数类型ArkUI_ListItemAlign <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：交叉轴方向的布局方式。参数类型ArkUI_ListItemAlign  |
| NODE_LIST_CHILDREN_MAIN_SIZE = 1003007 | 设置List子组件默认主轴尺寸。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> object: 参数格式为[ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md).<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .object: 参数格式为[ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md). |
| NODE_LIST_INITIAL_INDEX = 1003008 | 设置当前List初次加载时视口起始位置显示的item的索引值，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32: 当前List初次加载时视口起始位置显示的item的索引值，默认值：0。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32: 当前List初次加载时视口起始位置显示的item的索引值，默认值：0。|
| NODE_LIST_DIVIDER = 1003009 | 设置ListItem分割线样式，默认无分割线，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32： 分割线颜色，0xargb类型；<br> .value[1].f32： 分割线宽；<br> .value[2].f32： 分割线距离列表侧边起始端的距离，单位vp；<br> .value[3].f32： 分割线距离列表侧边结束端的距离，单位vp。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32： 分割线颜色，0xargb类型；<br> .value[1].f32： 分割线宽；<br> .value[2].f32： 分割线距离列表侧边起始端的距离，单位vp；<br> .value[3].f32： 分割线距离列表侧边结束端的距离，单位vp。 |
| NODE_LIST_SCROLL_TO_INDEX_IN_GROUP = 1003010 | 滑动到指定ListItemGroup中指定index。开启smooth动效时，会对经过的所有item进行加载和布局计算，当大量加载item时会导致性能问题。<br> <br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：要滑动到的目标ListItemGroup在当前List中的索引值。<br> .value[1].i32：要滑动到的目标ListItem在ListItemGroup中的索引值。<br> .value[2]?.i32：设置滑动到列表项在列表中的索引值时是否有动效，1表示有动效，0表示没有动效。默认值：0。<br> .value[3]?.i32：指定滑动到的元素与当前容器的对齐方式，参数类型[ArkUI_ScrollAlignment](capi-native-type-h.md#arkui_scrollalignment), 默认值：ARKUI_SCROLL_ALIGNMENT_START。<br>**起始版本：** 15  |
| NODE_LIST_LANES = 1003011 | 设置List列数，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32： List列数，如果设置了最大最小列宽，则设置列数不生效；<br> .value[1]?.f32：最小列宽，单位vp；<br> .value[2]?.f32：最大列宽，单位vp；<br> .value[3]?.f32：列间距，单位vp；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32： 当前List列数；<br> .value[1].f32： 最小列宽，单位vp；<br> .value[2].f32： 最小列宽，单位vp；<br> .value[3].f32： 列间距，单位vp。<br>**起始版本：** 15  |
| NODE_LIST_SCROLL_SNAP_ALIGN = 1003012 | 设置List限位对齐模式。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： List组件限位滚动时的对其方式，数据类型[ArkUI_ScrollSnapAlign](capi-native-type-h.md#arkui_scrollsnapalign)，默认值ARKUI_SCROLL_SNAP_ALIGN_NONE；<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32： List组件限位滚动时的对其方式，数据类型[ArkUI_ScrollSnapAlign](capi-native-type-h.md#arkui_scrollsnapalign)；<br>**起始版本：** 15   |
| NODE_LIST_MAINTAIN_VISIBLE_CONTENT_POSITION = 1003013 | 设置List显示区域外插入或删除数据是否保持可见内容位置不变。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：List显示区域外插入或删除数据是否保持可见内容位置不变。0表示不保持可见内容位置，1表示保持可见内容位置，默认值为0。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：List显示区域外插入或删除数据是否保持可见内容位置不变。0表示不保持可见内容位置，1表示保持可见内容位置，默认值为0。 <br>**起始版本：** 15   |
| NODE_LIST_STACK_FROM_END = 1003014 | 设置List从末尾开始布局。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：设置List是否从末尾开始布局。0表示从顶部开始布局，1表示从末尾开始布局，默认值为0。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：设置List是否从末尾开始布局。0表示从顶部开始布局，1表示从末尾开始布局，默认值为0。<br>**起始版本：** 19   |
| NODE_LIST_FOCUS_WRAP_MODE = 1003015 | List组件走焦换行模式，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：List组件走焦换行模式，参数类型[ArkUI_FocusWrapMode](capi-native-type-h.md#arkui_focuswrapmode)。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32: List组件走焦换行模式，参数类型[ArkUI_FocusWrapMode](capi-native-type-h.md#arkui_focuswrapmode)。<br>**起始版本：** 20  |
| NODE_LIST_SYNC_LOAD = 1003016 | List组件是否同步加载子节点，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：List组件是否同步加载子节点。0：分帧加载，1：同步加载。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32: List组件是否同步加载子节点。0：分帧加载，1：同步加载。<br>**起始版本：** 20   |
| NODE_SWIPER_LOOP = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SWIPER | Swiper是否开启循环，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：控制是否开启循环，0表示不循环，1表示循环，默认值为1。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：控制是否开启循环，0表示不循环，1表示循环，默认值为1。   |
| NODE_SWIPER_AUTO_PLAY | Swiper子组件是否自动播放，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：控制子组件是否自动播放，0表示不自动播放，1表示自动播放，默认值为0。 <br> .value[1]?.i32：手指按下是否停止自动播放，0表示停止，1表示不停止，默认值为0。该参数从API version 16开始支持。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：控制子组件是否自动播放，0表示不自动播放，1表示自动播放，默认值为0。 <br> .value[1].i32：手指按下是否停止自动播放，0表示停止，1表示不停止。该参数从API version 16开始支持。  |
| NODE_SWIPER_SHOW_INDICATOR | Swiper是否显示导航点指示器，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：是否显示导航点指示器，0表示不显示导航点指示器，1表示显示导航点指示器，默认值为1。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：是否显示导航点指示器，0表示不显示导航点指示器，1表示显示导航点指示器，默认值为1。  |
| NODE_SWIPER_INTERVAL | 设置Swiper自动播放时播放的时间间隔，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：使用自动播放时播放的时间间隔，单位为毫秒。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：使用自动播放时播放的时间间隔，单位为毫秒。  |
| NODE_SWIPER_VERTICAL | 设置Swiper是否为纵向滑动，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：是否为纵向滑动，0表示横向滑动，1表示纵向滑动，默认值为0。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：是否为纵向滑动，0表示横向滑动，1表示纵向滑动，默认值为0。  |
| NODE_SWIPER_DURATION | 设置Swiper子组件切换的动画时长，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：子组件切换的动画时长，单位为毫秒, 默认值为400。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：子组件切换的动画时长，单位为毫秒, 默认值为400。  |
| NODE_SWIPER_CURVE | 设置Swiper的动画曲线，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：设置动画曲线参数，参数类型[ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve)，默认值为ARKUI_CURVE_LINEAR。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：设置动画曲线参数，参数类型[ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve)，默认值为ARKUI_CURVE_LINEAR。 |
| NODE_SWIPER_ITEM_SPACE | 设置Swiper子组件与子组件之间间隙，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：子组件与子组件之间间隙数值。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：子组件与子组件之间间隙数值。  |
| NODE_SWIPER_INDEX | 设置Swiper当前在容器中显示的子组件的索引值，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：子组件的索引值。 <br> .value[1]?.i32：跳转动画模式，参数类型[ArkUI_SwiperAnimationMode](capi-native-type-h.md#arkui_swiperanimationmode)。仅当次调用有效。 <br> 该参数从API version 15开始支持。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：子组件的索引值。 |
| NODE_SWIPER_DISPLAY_COUNT | 设置Swiper一页内元素显示个数，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：视窗内显示的子元素个数。 <br> .value[1]?.i32：是否按组翻页，0：按子元素翻页，1：视窗内显示的子元素按组翻页，默认值：0。 <br> .string?: 此参数只能设置为“auto”。当设置为“auto”时，value[] 参数将被忽略。 <br> 该参数从API version 19开始支持。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：视窗内显示的子元素个数。 <br> .value[1].i32：是否按组翻页。该参数从API version 19开始支持。  |
| NODE_SWIPER_DISABLE_SWIPE | 设置Swiper禁用组件滑动切换功能，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：是否禁用组件滑动切换功能，0表示不禁用滑动切换功能，1表示禁用滑动切换功能，默认值为0。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：是否禁用组件滑动切换功能，0表示不禁用滑动切换功能，1表示禁用滑动切换功能，默认值为0。  |
| NODE_SWIPER_SHOW_DISPLAY_ARROW | 设置Swiper是否显示导航点箭头，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：设置是否显示导航点箭头，参数类型[ArkUI_SwiperArrow](capi-native-type-h.md#arkui_swiperarrow)，默认值为ARKUI_SWIPER_ARROW_HIDE。 <br> .?object：显示导航箭头时设置箭头样式，参数类型为[ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)。该参数从API version 19开始支持。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：设置是否显示导航点箭头，参数类型[ArkUI_SwiperArrow](capi-native-type-h.md#arkui_swiperarrow)， <br> .object：箭头样式，参数类型为[ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)。该参数从API version 19开始支持。 |
| NODE_SWIPER_EDGE_EFFECT_MODE | 设置Swiper的边缘滑动效果，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32: 边缘滑动效果，参数类型[ArkUI_EdgeEffect](capi-native-type-h.md#arkui_edgeeffect)， <br> 默认值为ARKUI_EDGE_EFFECT_SPRING。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32: 边缘滑动效果，参数类型[ArkUI_EdgeEffect](capi-native-type-h.md#arkui_edgeeffect)，  |
| NODE_SWIPER_NODE_ADAPTER | swiper组件适配器，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .object：使用[ArkUI_NodeAdapter](capi-arkui-nativemodule-arkui-nodeadapter8h.md)对象作为适配器。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .object：返回值格式为[ArkUI_NodeAdapter](capi-arkui-nativemodule-arkui-nodeadapter8h.md)。|
| NODE_SWIPER_CACHED_COUNT | swiper组件Adapter缓存数量，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：配合swiper组件Adapter使用，设置adapter中的缓存数量<br> .value[1]?.i32：是否显示缓存节点，0：不显示，1：显示，默认值：0。该参数从API version 19开始支持。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：adapter中的缓存数量。 <br> .value[1].i32：是否显示缓存节点，0：不显示，1：显示。该参数从API version 19开始支持。  |
| NODE_SWIPER_PREV_MARGIN | 设置 Swiper 组件的前边距，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：前边距数值，单位为vp，默认值为0。 <br> .value[1]?.i32：是否忽略空白，1表示忽略空白，0表示不忽略空白。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：前边距数值，单位为vp。.value[1].i32：是否忽略空白，1表示忽略空白，0表示不忽略空白。 |
| NODE_SWIPER_NEXT_MARGIN | 设置 Swiper 组件的后边距，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：后边距数值，单位为vp，默认值为0。 <br> .value[1]?.i32：是否忽略空白，1表示忽略空白，0表示不忽略空白。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：后边距数值，单位为vp。.value[1].i32：是否忽略空白，1表示忽略空白，0表示不忽略空白。  |
| NODE_SWIPER_INDICATOR | 设置 Swiper 组件的导航指示器类型，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：设置导航指示器的类型，参数类型[ArkUI_SwiperIndicatorType](capi-native-type-h.md#arkui_swiperindicatortype)。 <br> .object：导航指示器的类型为ARKUI_SWIPER_INDICATOR_TYPE_DOT时参数类型为[ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)。 <br>          导航指示器的类型为ARKUI_SWIPER_INDICATOR_TYPE_DIGIT时参数类型为[ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)。 <br>          ArkUI_SwiperDigitIndicator类型从API version 19开始支持属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：导航指示器的类型，参数类型[ArkUI_SwiperIndicatorType](capi-native-type-h.md#arkui_swiperindicatortype)。 <br> .object：导航指示器的类型为ARKUI_SWIPER_INDICATOR_TYPE_DOT时参数类型为[ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)。 <br>          导航指示器的类型为ARKUI_SWIPER_INDICATOR_TYPE_DIGIT时参数类型为[ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)。 <br>          ArkUI_SwiperDigitIndicator类型从API version 19开始支持  |
| NODE_SWIPER_NESTED_SCROLL | 设置Swiper组件和父组件的嵌套滚动模式。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：Swiper组件和父组件的嵌套滚动模式，参数类型[ArkUI_SwiperNestedScrollMode](capi-native-type-h.md#arkui_swipernestedscrollmode) <br> 默认值为：ARKUI_SWIPER_NESTED_SRCOLL_SELF_ONLY <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：Swiper组件和父组件的嵌套滚动模式，参数类型[ArkUI_SwiperNestedScrollMode](capi-native-type-h.md#arkui_swipernestedscrollmode)   |
| NODE_SWIPER_SWIPE_TO_INDEX | 设置swiper组件翻至指定页面。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：指定页面在Swiper中的索引值。<br> .value[1]?.i32：设置翻至指定页面时是否有动效。1表示有动效，0表示没有动效, 默认值：0。 |
| NODE_SWIPER_INDICATOR_INTERACTIVE | 设置禁用组件导航点交互功能。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：设置禁用组件导航点交互功能，设置为true时表示导航点可交互，默认值true。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：设置禁用组件导航点交互功能。  |
| NODE_SWIPER_PAGE_FLIP_MODE | 设置组件鼠标滚轮翻页模式。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：设置组件鼠标滚轮翻页模式，参数类型[ArkUI_PageFlipMode](capi-native-type-h.md#arkui_pageflipmode)。<br> 属性获取方法返回值[ArkUI_PageFlipMode](capi-native-type-h.md#arkui_pageflipmode)格式： <br> .value[0].i32：鼠标滚轮翻页模式。 <br>**起始版本：** 15   |
| NODE_SWIPER_AUTO_FILL | 设置Swiper一页内元素显示个数根据元素最小宽度自适应，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：元素显示最小宽度，单位：vp。 <br> .value[1]?.i32：是否按组翻页，0：按子元素翻页，1：视窗内显示的子元素按组翻页，默认值：0 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：元素显示最小宽度，单位：vp。 <br> .value[1].i32：是否按组翻页。 <br>**起始版本：** 19  |
| NODE_SWIPER_MAINTAIN_VISIBLE_CONTENT_POSITION = 1001023 | 设置Swiper显示区域外插入或删除数据是否保持可见内容位置不变。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：Swiper显示区域外插入或删除数据是否保持可见内容位置不变。0表示不保持可见内容位置，1表示保持可见内容位置，默认值为0。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：Swiper显示区域外插入或删除数据是否保持可见内容位置不变。0表示不保持可见内容位置，1表示保持可见内容位置，默认值为0。 <br>**起始版本：** 20   |
| NODE_LIST_ITEM_SWIPE_ACTION = MAX_NODE_SCOPE_NUM * ARKUI_NODE_LIST_ITEM | 设置ListItem的划出组件，支持属性设置，属性重置，属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .object：使用[ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)对象构造。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .object：使用[ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)对象构造。 |
| NODE_LIST_ITEM_GROUP_SET_HEADER = MAX_NODE_SCOPE_NUM * ARKUI_NODE_LIST_ITEM_GROUP | 设置 ListItemGroup 头部组件，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .object：使用[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)对象作为ListItemGroup头部组件。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .object：使用[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)对象作为ListItemGroup头部组件。 |
| NODE_LIST_ITEM_GROUP_SET_FOOTER | 设置 ListItemGroup 尾部组件，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .object：使用[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)对象作为ListItemGroup尾部组件。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .object：使用[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)对象作为ListItemGroup尾部组件。|
| NODE_LIST_ITEM_GROUP_SET_DIVIDER | 设置ListItem分割线样式，默认无分割线，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32： 颜色，0xargb类型；<br> .value[1].f32： 分割线宽，单位vp；<br> .value[2].f32： 分割线距离列表侧边起始端的距离，单位vp；<br> .value[3].f32： 分割线距离列表侧边结束端的距离，单位vp。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].u32： 颜色，0xargb类型；<br> .value[1].f32： 分割线宽，单位vp；<br> .value[2].f32： 分割线距离列表侧边起始端的距离，单位vp；<br> .value[3].f32： 分割线距离列表侧边结束端的距离，单位vp。 |
| NODE_LIST_ITEM_GROUP_CHILDREN_MAIN_SIZE = 1005003 | 设置ListItemGroup子组件默认主轴尺寸。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> object: 参数格式为[ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md).<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .object: 参数格式为[ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md). |
| NODE_LIST_ITEM_GROUP_NODE_ADAPTER = 1005004 | ListItemGroup组件适配器，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .object：使用[ArkUI_NodeAdapter](capi-arkui-nativemodule-arkui-nodeadapter8h.md)对象作为适配器。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .object：返回值格式为[ArkUI_NodeAdapter](capi-arkui-nativemodule-arkui-nodeadapter8h.md)。 <br>**起始版本：** 15   |
| NODE_COLUMN_ALIGN_ITEMS = MAX_NODE_SCOPE_NUM * ARKUI_NODE_COLUMN | 设置Column子组件在水平方向上的对齐格式，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：子组件在水平方向上的对齐格式，数据类型[ArkUI_HorizontalAlignment](capi-native-type-h.md#arkui_horizontalalignment)， <br> 默认值ARKUI_HORIZONTAL_ALIGNMENT_CENTER。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：子组件在水平方向上的对齐格式，数据类型[ArkUI_HorizontalAlignment](capi-native-type-h.md#arkui_horizontalalignment)。  |
| NODE_COLUMN_JUSTIFY_CONTENT | 设置Column子组件在垂直方向上的对齐格式，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：子组件在垂直方向上的对齐格式，数据类型[ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment)， <br> 默认值ARKUI_FLEX_ALIGNMENT_START。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：子组件在垂直方向上的对齐格式，数据类型[ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment)。  |
| NODE_ROW_ALIGN_ITEMS = MAX_NODE_SCOPE_NUM * ARKUI_NODE_ROW | 设置Row子组件在垂直方向上的对齐格式，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：子组件在垂直方向上的对齐格式，数据类型[ArkUI_VerticalAlignment](capi-native-type-h.md#arkui_verticalalignment)， <br> 默认值ARKUI_VERTICAL_ALIGNMENT_CENTER。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：子组件在垂直方向上的对齐格式，数据类型[ArkUI_VerticalAlignment](capi-native-type-h.md#arkui_verticalalignment)。  |
| NODE_ROW_JUSTIFY_CONTENT | 设置Row子组件在水平方向上的对齐格式，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：子组件在水平方向上的对齐格式，数据类型[ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment)， <br> 默认值ARKUI_FLEX_ALIGNMENT_START。 <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：子组件在水平方向上的对齐格式，数据类型[ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment)。   |
| NODE_FLEX_OPTION = MAX_NODE_SCOPE_NUM * ARKUI_NODE_FLEX | 设置Flex属性，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0]?.i32：子组件在Flex容器上排列的方向[ArkUI_FlexDirection](capi-native-type-h.md#arkui_flexdirection)，默认值为ARKUI_FLEX_DIRECTION_ROW； <br> .value[1]?.i32：排列规则[ArkUI_FlexWrap](capi-native-type-h.md#arkui_flexwrap)，默认值为ARKUI_FLEX_WRAP_NO_WRAP； <br> .value[2]?.i32：主轴上的对齐格式[ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment)，默认值为ARKUI_FLEX_ALIGNMENT_START； <br> .value[3]?.i32：交叉轴上的对齐格式[ArkUI_ItemAlignment](capi-native-type-h.md#arkui_itemalignment)，默认值为ARKUI_ITEM_ALIGNMENT_START； <br> .value[4]?.i32：	交叉轴中有额外的空间时，多行内容的对齐方式[ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment)，默认值为ARKUI_FLEX_ALIGNMENT_START； <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：子组件在Flex容器上排列的方向的枚举值； <br> .value[1].i32：排列规则的枚举值； <br> .value[2].i32：主轴上的对齐格式的枚举值； <br> .value[3].i32：交叉轴上的对齐格式的枚举值； <br> .value[4].i32：交叉轴中有额外的空间时，多行内容的对齐方式的枚举值；  |
| NODE_REFRESH_REFRESHING = MAX_NODE_SCOPE_NUM * ARKUI_NODE_REFRESH | 设置组件是否正在刷新，支持属性设置，属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].i32：参数类型为1或者0。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：参数类型为1或者0。 |
| NODE_REFRESH_CONTENT | 设置下拉区域的自定义内容，支持属性设置和重置。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .object：参数类型[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。  |
| NODE_REFRESH_PULL_DOWN_RATIO = 1009002 | 设置下拉跟手系数，支持属性设置，属性重置和属性获取接口。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].f32：下拉跟手系数,有效值为0-1之间的值。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：下拉跟手系数,有效值为0-1之间的值。   |
| NODE_REFRESH_OFFSET = 1009003 | 设置触发刷新的下拉偏移量，支持属性设置，属性重置和属性获取接口。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].f32：下拉偏移量，单位vp， 默认值：64vp。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：下拉偏移量，单位vp， 默认值：64vp。   |
| NODE_REFRESH_PULL_TO_REFRESH = 1009004 | 设置当下拉距离超过refreshOffset时是否触发刷新，支持属性设置，属性重置和属性获取接口。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].i32：是否触发刷新，true为触发刷新，false为不触发刷新。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：是否触发刷新，1为触发刷新，0为不触发刷新。 |
| NODE_REFRESH_MAX_PULL_DOWN_DISTANCE = 1009005 | 设置刷新的最大下拉距离。此属性可以根据需要通过api进行属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)的参数格式:<br> .value[0].f32: 最大下拉距离, 单位：vp。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)的格式:<br> .value[0].f32: 最大下拉距离, 单位：vp。<br>**起始版本：** 20   |
| NODE_WATER_FLOW_LAYOUT_DIRECTION = MAX_NODE_SCOPE_NUM * ARKUI_NODE_WATER_FLOW | 定义瀑布流组件布局主轴方向，支持属性设置、重置和获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].i32 主轴方向，参数类型[ArkUI_FlexDirection](capi-native-type-h.md#arkui_flexdirection)。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32 主轴方向，参数类型[ArkUI_FlexDirection](capi-native-type-h.md#arkui_flexdirection)。 |
| NODE_WATER_FLOW_COLUMN_TEMPLATE | 设置当前瀑布流组件布局列的数量，不设置时默认1列，支持属性设置、重置和获取。例如，'1fr 1fr 2fr' 是将父组件分3列，将父组件允许的宽分为4等份，第1列占1份，第2列占1份，第3列占2份。可使用columnsTemplate('repeat(auto-fill,track-size)')根据给定的列宽track-size自动计算列数，其中repeat、auto-fill为关键字，track-size为可设置的宽度，支持的单位包括px、vp、%或有效数字，默认单位为vp。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .string: 布局列的数量.<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .string: 布局列的数量.   |
| NODE_WATER_FLOW_ROW_TEMPLATE | 设置当前瀑布流组件布局行的数量，不设置时默认1行，支持属性设置、重置和获取。例如，'1fr 1fr 2fr'是将父组件分3行，将父组件允许的高分为4等份，第1行占1份，第2行占1份，第3行占2份。可使用rowsTemplate('repeat(auto-fill,track-size)')根据给定的行高track-size自动计算行数，其中repeat、auto-fill为关键字，track-size为可设置的高度，支持的单位包括px、vp、%或有效数字，默认单位为vp。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .string: 布局行的数量.<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .string: 布局行的数量.  |
| NODE_WATER_FLOW_COLUMN_GAP | 设置列与列的间距，支持属性设置、重置和获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].f32: 列与列的间距, 单位vp.<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32: 列与列的间距, 单位vp. |
| NODE_WATER_FLOW_ROW_GAP | 设置行与行的间距，支持属性设置、重置和获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].f32: 行与行的间距, 单位vp.<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32: 行与行的间距, 单位vp. |
| NODE_WATER_FLOW_SECTION_OPTION | 设置FlowItem分组配置信息，支持属性设置、重置和获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].i32: 从0开始计算的索引，会转换为整数，表示要开始改变分组的位置.<br> .object: 参数格式为[ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md).<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .object: 返回值格式为[ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md). |
| NODE_WATER_FLOW_NODE_ADAPTER | waterFlow组件适配器，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .object：使用[ArkUI_NodeAdapter](capi-arkui-nativemodule-arkui-nodeadapter8h.md)对象作为适配器。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .object: 返回值格式为[ArkUI_NodeAdapter](capi-arkui-nativemodule-arkui-nodeadapter8h.md).  |
| NODE_WATER_FLOW_CACHED_COUNT | waterFlow组件Adapter缓存数量，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：配合waterFlow组件Adapter使用，设置adapter中的缓存数量<br> .value[1]?.i32：是否显示缓存节点，0：不显示，1：显示，默认值：0。该参数从API version 16开始支持。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：adapter中的缓存数量。<br> .value[1].i32：是否显示缓存节点，0：不显示，1：显示。该参数从API version 16开始支持。  |
| NODE_WATER_FLOW_FOOTER | 设置瀑布流组件末尾的自定义显示组件。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .object：参数类型[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。   |
| NODE_WATER_FLOW_SCROLL_TO_INDEX | 滑动到指定index。开启smooth动效时，会对经过的所有item进行加载和布局计算，当大量加载item时会导致性能问题。<br> <br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：要滑动到的目标元素在当前容器中的索引值。<br> .value[1]?.i32：设置滑动到列表项在列表中的索引值时是否有动效，1表示有动效，0表示没有动效。默认值：0。<br> .value[2]?.i32：指定滑动到的元素与当前容器的对齐方式，参数类型[ArkUI_ScrollAlignment](capi-native-type-h.md#arkui_scrollalignment)。默认值为：ARKUI_SCROLL_ALIGNMENT_START。|
| NODE_WATER_FLOW_ITEM_CONSTRAINT_SIZE | 设置当前瀑布流子组件的约束尺寸属性，组件布局时，进行尺寸范围限制，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：最小宽度，使用-1表示不设置； <br> .value[1].f32：最大宽度，使用-1表示不设置； <br> .value[2].f32：最小高度，使用-1表示不设置； <br> .value[3].f32：最大高度，使用-1表示不设置； <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32：最小宽度，使用-1表示不设置； <br> .value[1].f32：最大宽度，使用-1表示不设置； <br> .value[2].f32：最小高度，使用-1表示不设置； <br> .value[3].f32：最大高度，使用-1表示不设置；  |
| NODE_WATER_FLOW_LAYOUT_MODE | 定义瀑布流组件布局模式，支持属性设置、重置和获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].i32 布局模式，参数类型[ArkUI_WaterFlowLayoutMode](capi-native-type-h.md#arkui_waterflowlayoutmode)。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32 布局模式，参数类型[ArkUI_WaterFlowLayoutMode](capi-native-type-h.md#arkui_waterflowlayoutmode)。<br>**起始版本：** 18   |
| NODE_WATER_FLOW_SYNC_LOAD = 1010012 | WaterFlow组件是否同步加载子节点，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：WaterFlow组件是否同步加载子节点。0：分帧加载，1：同步加载。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32: WaterFlow组件是否同步加载子节点。0：分帧加载，1：同步加载。<br>**起始版本：** 20   |
| NODE_RELATIVE_CONTAINER_GUIDE_LINE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_RELATIVE_CONTAINER | 设置RelativeContaine容器内的辅助线，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .object: RelativeContaine容器内的辅助线： <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .object: RelativeContaine容器内的辅助线：  |
| NODE_RELATIVE_CONTAINER_BARRIER | 设置RelativeContaine容器内的屏障，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .object: RelativeContaine容器内的辅助线： <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .object: RelativeContaine容器内的屏障：   |
| NODE_GRID_COLUMN_TEMPLATE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_GRID | 设置当前Grid组件布局列的数量，不设置时默认1列，支持属性设置、重置和获取。例如，'1fr 1fr 2fr' 是将父组件分3列，将父组件允许的宽分为4等份，第1列占1份，第2列占1份，第3列占2份。可使用columnsTemplate('repeat(auto-fill,track-size)')根据给定的列宽track-size自动计算列数，其中repeat、auto-fill为关键字，track-size为可设置的宽度，支持的单位包括px、vp、%或有效数字，默认单位为vp。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .string: 布局列的数量.<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .string: 布局列的数量. |
| NODE_GRID_ROW_TEMPLATE | 设置当前Grid布局行的数量或最小行高值，不设置时默认1行，支持属性设置、重置和获取。例如，'1fr 1fr 2fr'是将父组件分3行，将父组件允许的高分为4等份，第1行占1份，第2行占1份，第3行占2份。可使用rowsTemplate('repeat(auto-fill,track-size)')根据给定的行高track-size自动计算行数，其中repeat、auto-fill为关键字，track-size为可设置的高度，支持的单位包括px、vp、%或有效数字，默认单位为vp。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .string: 布局行的数量.<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .string: 布局行的数量. |
| NODE_GRID_COLUMN_GAP | 设置列与列的间距，支持属性设置、重置和获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].f32: 列与列的间距, 单位vp.<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32: 列与列的间距, 单位vp. |
| NODE_GRID_ROW_GAP | 设置行与行的间距，支持属性设置、重置和获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式： <br> .value[0].f32: 行与行的间距, 单位vp.<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].f32: 行与行的间距, 单位vp. |
| NODE_GRID_NODE_ADAPTER | Grid组件适配器，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .object：使用[ArkUI_NodeAdapter](capi-arkui-nativemodule-arkui-nodeadapter8h.md)对象作为适配器。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .object: 返回值格式为[ArkUI_NodeAdapter](capi-arkui-nativemodule-arkui-nodeadapter8h.md). |
| NODE_GRID_CACHED_COUNT | Grid组件Adapter缓存数量，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：配合Grid组件Adapter使用，设置Adapter中的缓存数量。 |
| NODE_GRID_FOCUS_WRAP_MODE = 1013006 | Grid组件走焦换行模式，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：Grid组件走焦换行模式，参数类型[ArkUI_FocusWrapMode](capi-native-type-h.md#arkui_focuswrapmode)。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32: Grid组件走焦换行模式，参数类型[ArkUI_FocusWrapMode](capi-native-type-h.md#arkui_focuswrapmode)。<br>**起始版本：** 20  |
| NODE_GRID_SYNC_LOAD = 1013007 | Grid组件是否同步加载子节点，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：Grid组件是否同步加载子节点。0：分帧加载，1：同步加载。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32: Grid组件是否同步加载子节点。0：分帧加载，1：同步加载。<br>**起始版本：** 20   |
| NODE_TEXT_PICKER_COLUMN_WIDTHS = 15009 | 设置每一个选择项列宽，支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32: 设置的第1个选择项列宽，为总宽度的百分比。默认情况下，所有选择项的列宽相等。<br> .value[1]?.f32: 设置的第2个选择项列宽，为总宽度的百分比。默认情况下，所有选择项的列宽相等。<br> .value[2]?.f32: 设置的第3个选择项列宽，为总宽度的百分比。默认情况下，所有选择项的列宽相等。<br> ...<br> .value[n]?.f32: 设置的第n+1个选择项列宽，为总宽度的百分比。默认情况下，所有选择项的列宽相等。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> value[0].f32: 第1列宽度，总宽度的百分比。<br> value[1].f32: 第2列宽度，总宽度的百分比。<br> value[2].f32: 第3列宽度，总宽度的百分比。<br> ...<br> value[n].f32: 第n+1列宽度，总宽度的百分比。<br>**起始版本：** 18  |
| NODE_IMAGE_ANIMATOR_IMAGES = ARKUI_NODE_IMAGE_ANIMATOR * MAX_NODE_SCOPE_NUM | 设置帧动画组件的图片帧信息集合。不支持动态更新。支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .size：图片帧的数量； <br> .object：图片帧数组，参数类型为[ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)数组； <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .size：图片帧的数量； <br> .object：图片帧数组，参数类型为[ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)数组；  |
| NODE_IMAGE_ANIMATOR_STATE = 19001 | 控制帧动画组件的播放状态。支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：控制动画的播放状态，参数类型为[ArkUI_AnimationStatus](capi-native-type-h.md#arkui_animationstatus)，默认值为初始状态。 <br>     属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：控制动画的播放状态，参数类型为[ArkUI_AnimationStatus](capi-native-type-h.md#arkui_animationstatus)。   |
| NODE_IMAGE_ANIMATOR_DURATION = 19002 | 设置帧动画的播放时长，当数组中任意一帧图片单独设置了duration属性后，该属性设置无效。支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：播放时长，单位为毫秒，默认值1000。 <br>     属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：播放时长，单位为毫秒，默认值1000。  |
| NODE_IMAGE_ANIMATOR_REVERSE = 19003 | 设置帧动画的播放方向。支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：播放方向，0表示从第一张图片播放到最后一张，1表示从最后一张图片播放到第一张，默认值为0。 <br>     属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：播放方向，0表示从第一张图片播放到最后一张，1表示从最后一张图片播放到第一张。  |
| NODE_IMAGE_ANIMATOR_FIXED_SIZE = 19004 | 设置图片大小是否固定为组件大小。支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：设置图片大小是否固定为组件大小，1表示图片大小与组件大小一致。0表示每一张图片的width、height、top和left都要单独设置，默认值为1。<br>     属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：设置图片大小是否固定为组件大小，1表示图片大小与组件大小一致。0表示每一张图片的width、height、top和left都要单独设置。  |
| NODE_IMAGE_ANIMATOR_FILL_MODE = 19005 | 设置帧动画在当前播放方向下，动画开始前和结束后的状态。支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：当前播放方向下，动画开始前和结束后的状态，参数类型为{ArkUI_AnimationFillMode}，默认值为FORWARDS。 <br>     属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：当前播放方向下，动画开始前和结束后的状态，参数类型为{ArkUI_AnimationFillMode}。  |
| NODE_IMAGE_ANIMATOR_ITERATION = 19006 | 设置帧动画的播放次数。支持属性设置，属性重置和属性获取接口。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：播放次数。 <br>     属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .value[0].i32：播放次数。   |
| NODE_EMBEDDED_COMPONENT_WANT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_EMBEDDED_COMPONENT | 定义用于启动EmbeddedAbility的want。支持属性设置。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .object: EmbeddedCompont的want参数。参数类型为[AbilityBase_Want](capi-arkui-nativemodule-abilitybase-want.md)。默认值为nullptr。 <br>**起始版本：** 20   |
| NODE_EMBEDDED_COMPONENT_OPTION | EmbeddedCompont的选项。支持属性设置。<br>属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <br> .object: EmbeddedCompont的选项列表，参数类型为[ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md)。<br>**起始版本：** 20   |

### ArkUI_NodeEventType

```
enum ArkUI_NodeEventType
```

**描述：**


提供NativeNode组件支持的事件类型定义。

**起始版本：** 12

| 枚举项 | 描述  |
| -- |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| NODE_TOUCH_EVENT = 0 | 手势事件类型。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)。 |
| NODE_EVENT_ON_APPEAR | 挂载事件。触发该事件的条件 ：组件挂载显示时触发此回调。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中不包含参数。 |
| NODE_EVENT_ON_DISAPPEAR | 卸载事件。触发该事件的条件 ：组件卸载时触发此回调。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中不包含参数。 |
| NODE_EVENT_ON_AREA_CHANGE | 组件区域变化事件触发该事件的条件：组件区域变化时触发该回调。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含12个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>：表示过去目标元素的宽度，类型为number，单位vp。<br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>：表示过去目标元素的高度，类型为number，单位vp。<br> <b>ArkUI_NodeComponentEvent.data[2].f32</b>：表示过去目标元素左上角相对父元素左上角的位置的x轴坐标，类型为number，单位vp。<br> <b>ArkUI_NodeComponentEvent.data[3].f32</b>：表示过去目标元素左上角相对父元素左上角的位置的y轴坐标，类型为number，单位vp。<br> <b>ArkUI_NodeComponentEvent.data[4].f32</b>：表示过去目标元素目标元素左上角相对页面左上角的位置的x轴坐标，类型为number，单位vp。<br> <b>ArkUI_NodeComponentEvent.data[5].f32</b>：表示过去目标元素目标元素左上角相对页面左上角的位置的y轴坐标，类型为number，单位vp。<br> <b>ArkUI_NodeComponentEvent.data[6].f32</b>：表示最新目标元素的宽度，类型为number，单位vp。<br> <b>ArkUI_NodeComponentEvent.data[7].f32</b>：表示最新目标元素的高度，类型为number，单位vp。<br> <b>ArkUI_NodeComponentEvent.data[8].f32</b>：表示最新目标元素左上角相对父元素左上角的位置的x轴坐标，类型为number，单位vp。<br> <b>ArkUI_NodeComponentEvent.data[9].f32</b>：表示最新目标元素左上角相对父元素左上角的位置的y轴坐标，类型为number，单位vp。<br> <b>ArkUI_NodeComponentEvent.data[10].f32</b>：表示最新目标元素目标元素左上角相对页面左上角的位置的x轴坐标，类型为number，单位vp。<br> <b>ArkUI_NodeComponentEvent.data[11].f32</b>：表示最新目标元素目标元素左上角相对页面左上角的位置的y轴坐标，类型为number，单位vp。 |
| NODE_ON_FOCUS | 获焦事件。触发该事件的条件：组件获焦时触发此回调。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中不包含参数。  |
| NODE_ON_BLUR | 失去焦点事件。触发该事件的条件：组件失去焦点时触发此回调。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中不包含参数。 |
| NODE_ON_CLICK | 组件点击事件。触发该事件的条件：组件被点击时触发此回调。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含8个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>：点击位置相对于被点击元素原始区域左上角的X坐标，单位px。<br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>：点击位置相对于被点击元素原始区域左上角的Y坐标，单位px。<br> <b>ArkUI_NodeComponentEvent.data[2].f32</b>：事件时间戳。触发事件时距离系统启动的时间间隔，单位微秒。<br> <b>ArkUI_NodeComponentEvent.data[3].i32</b>：事件输入设备，1表示鼠标，2表示触屏，4表示按键。<br> <b>ArkUI_NodeComponentEvent.data[4].f32</b>：点击位置相对于应用窗口左上角的X坐标，单位px。<br> <b>ArkUI_NodeComponentEvent.data[5].f32</b>：点击位置相对于应用窗口左上角的Y坐标，单位px。<br> <b>ArkUI_NodeComponentEvent.data[6].f32</b>：点击位置相对于应用屏幕左上角的X坐标，单位px。<br> <b>ArkUI_NodeComponentEvent.data[7].f32</b>：点击位置相对于应用屏幕左上角的Y坐标，单位px。  |
| NODE_ON_TOUCH_INTERCEPT | 组件自定义事件拦截。触发该事件的条件：组件被触摸时触发此回调。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)。  |
| NODE_EVENT_ON_VISIBLE_AREA_CHANGE | 组件可见区域变化事件。触发该事件的条件：组件可见面积与自身面积的比值接近设置的阈值时触发回调，注册事件前需先使用NODE_VISIBLE_AREA_CHANGE_RATIO 配置阈值。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>：组件可见面积与自身面积的比值与上次变化相比的情况，变大为1，变小为0。<br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>：触发回调时组件可见面积与自身面积的比值。  |
| NODE_ON_HOVER | 鼠标进入或退出组件事件。触发该事件的条件：鼠标进入或退出组件时触发回调。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>：鼠标是否悬浮在组件上，鼠标进入时为1，退出时为0。  |
| NODE_ON_MOUSE | 组件点击事件。触发该事件的条件：组件被鼠标按键点击或者鼠标在组件上悬浮移动时触发该回调。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)。 |
| NODE_EVENT_ON_ATTACH | 上树事件。触发该事件的条件 ：组件上树时触发此回调。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中不包含参数。 |
| NODE_EVENT_ON_DETACH | 下树事件。触发该事件的条件 ：组件下树时触发此回调。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中不包含参数。  |
| NODE_ON_ACCESSIBILITY_ACTIONS = 13 | 无障碍支持操作事件触发。触发该事件的条件：已设置无障碍操作类型，并进行相应操作。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数: <br> <b>ArkUI_NodeComponentEvent.data[0].u32</b>: 触发回调的操作类型，参数类型[ArkUI_AccessibilityActionType](capi-native-type-h.md#arkui_accessibilityactiontype)。   |
| NODE_ON_PRE_DRAG = 14 | 在拖拽行为开始之前告诉侦听器详细的交互状态。触发该事件的条件：组件可拖拽，当长按浮起/松手/发起拖拽时，回调触发。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>：对应ArkUI_PreDragStatus。   |
| NODE_ON_DRAG_START = 15 | 用户已移动足够距离，即将发起拖拽。触发该事件的条件：长按拖动产生足够位移距离时触发。<br> 事件回调发生时，可从事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中获取ArkUI_DragEvent。  |
| NODE_ON_DRAG_ENTER = 16 | 用户拖拽进入当前组件范围。触发该事件的条件: 拖拽对象进入监听了该事件的组件边界时触发。<br> 事件回调发生时，可从事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中获取ArkUI_DragEvent。 |
| NODE_ON_DRAG_MOVE = 17 | 用户拖拽在当前组件范围内移动。触发该事件的条件: 拖拽对象在监听了该事件的组件范围内移动时触发。<br> 事件回调发生时，可从事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中获取ArkUI_DragEvent。    |
| NODE_ON_DRAG_LEAVE = 18 | 用户拖拽从当前组件范围离开。触发该事件的条件: 拖拽对象离开监听了该事件的组件边界时触发。<br> 事件回调发生时，可从事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中获取ArkUI_DragEvent。  |
| NODE_ON_DROP = 19 | 当用户在组件上方松手时，该组件上可通过该回调拿到拖拽数据进行处理。触发该事件的条件: 拖拽对象并在组件上方松手时触发。<br> 事件回调发生时，可从事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中获取ArkUI_DragEvent。  |
| NODE_ON_DRAG_END = 20 | 拖拽发起方可通过注册该回调感知拖拽结束后的结果。触发该事件的条件：用户松手，拖拽行为结束时触发。事件回调发生时，可从事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中获取ArkUI_DragEvent。  |
| NODE_ON_KEY_EVENT = 21 | 绑定该方法的组件获焦后，按键动作触发该回调。触发该事件的条件 ：由外设键盘等设备与获焦窗口交互触发此回调。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br>**起始版本：** 14  |
| NODE_ON_KEY_PRE_IME = 22 | 绑定该方法的组件获焦后，按键动作在响应输入法前优先触发该回调。该回调的返回值为true时，视作该按键事件已被消费，后续的事件回调（keyboardShortcut、输入法事件、onKeyEvent）会被拦截，不再触发。触发该事件的条件 ：由外设键盘等设备与获焦窗口交互触发此回调。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br>**起始版本：** 14     |
| NODE_ON_FOCUS_AXIS = 23 | 绑定该方法的组件获焦后，收到焦点轴事件时触发该回调。触发该事件的条件 ：由游戏手柄与获焦组件交互触发此回调。 <br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)。 <br>**起始版本：** 15    |
| NODE_DISPATCH_KEY_EVENT = 24 | 组件按键事件重新派发事件。当组件节点接收到按键事件时，将触发此回调函数，而非将事件分发给其子节点。 <br> 当事件回调发生时，[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) 对象中的联合类型为 [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。 <br>**起始版本：** 15    |
| NODE_ON_AXIS = 25 | 绑定该方法的组件收到轴事件时触发该回调。当绑定组件接收到轴事件时，会触发该事件回调。 <br> 事件发生时，[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) 对象中的联合类型为[ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)。 <br>**起始版本：** 17  |
| NODE_ON_HOVER_EVENT = 27 | 定义鼠标指针移至组件上方或远离组件时触发的事件。当鼠标指针移到组件上方或远离组件时触发该事件。 <br>当事件回调发生时，[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合类型为[ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md).  <br>     **起始版本：** 17  |
| NODE_ON_CLICK_EVENT = 26 | 绑定该方法的组件被点击时触发此回调。当绑定组件被点击时，将触发此事件回调。   <br> 当发生事件回调，[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合类型是[ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)。  <br>**起始版本：** 18   |
| NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_EVENT = 28 | 设置限制回调间隔的NODE_EVENT_ON_VISIBLE_AREA_CHANGE事件的回调。触发该事件的条件：组件可见面积与自身面积的比值接近设置的阈值时触发回调，注册事件前需先使用NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_RATIO 配置阈值和更新间隔。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>：组件可见面积与自身面积的比值与上次变化相比的情况，变大为1，变小为0。<br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>：触发回调时组件可见面积与自身面积的比值。<br>**起始版本：** 17  |
| NODE_ON_HOVER_MOVE = 29 | 定义悬浮事件。当手写笔设备指针悬停在组件内时会触发该事件。<br> 事件回调发生时, 可从事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中获取[ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)。<br>**起始版本：** 15   |
| NODE_TEXT_ON_DETECT_RESULT_UPDATE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT | 文本设置TextDataDetectorConfig且识别成功时，触发onDetectResultUpdate回调。触发该事件的条件：文本设置TextDataDetectorConfig且识别成功后。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)。<br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)中包含1个参数：<br> <b>ArkUI_StringAsyncEvent.pStr</b>：表示文本识别的结果，Json格式。  |
| NODE_TEXT_SPAN_ON_LONG_PRESS = 1001 | Span组件长按事件。组件被长按时触发此回调。<br> 事件回调发生时，可从事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中获取ArkUI_UIInputEvent。<br>**起始版本：** 20   |
| NODE_IMAGE_ON_COMPLETE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_IMAGE | 图片加载成功事件。触发该事件的条件 ：图片数据加载成功和解码成功均触发该回调。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含9个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>：表示加载状态，0表示数据加载成功，1表示解码成功。<br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>：表示图片的宽度，单位px。<br> <b>ArkUI_NodeComponentEvent.data[2].f32</b>：表示图片的高度，单位px。<br> <b>ArkUI_NodeComponentEvent.data[3].f32</b>：表示当前组件的宽度，单位px。<br> <b>ArkUI_NodeComponentEvent.data[4].f32</b>：表示当前组件的高度，单位px。<br> <b>ArkUI_NodeComponentEvent.data[5].f32</b>：图片绘制区域相对组件X轴位置，单位px。<br> <b>ArkUI_NodeComponentEvent.data[6].f32</b>：图片绘制区域相对组件Y轴位置，单位px。<br> <b>ArkUI_NodeComponentEvent.data[7].f32</b>：图片绘制区域宽度，单位px。<br> <b>ArkUI_NodeComponentEvent.data[8].f32</b>：图片绘制区域高度，单位px。  |
| NODE_IMAGE_ON_ERROR | 图片加载失败事件。触发该事件的条件：图片加载异常时触发该回调。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>错误码信息：<br> 401: 图片路径参数异常，无法获取到图片数据。<br> 103101: 图片格式不支持。  |
| NODE_IMAGE_ON_SVG_PLAY_FINISH | SVG图片动效播放完成事件。触发该事件的条件：带动效的SVG图片动画结束时触发。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中不包含参数。  |
| NODE_IMAGE_ON_DOWNLOAD_PROGRESS | 定义图片下载过程中触发事件。触发该事件的条件 ：页面组件下载网页图片时触发。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数: <br> <b>ArkUI_NodeComponentEvent.data[0].u32</b>: 到目前为止已下载的字节数。 <br> <b>ArkUI_NodeComponentEvent.data[1].u32</b>: 要下载图片的总字节数。  |
| NODE_TOGGLE_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TOGGLE | 开关状态发生变化时触发给事件。触发该事件的条件：开关状态发生变化。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>：当前开关状态，1表示开，0表示关。   |
| NODE_TEXT_INPUT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_INPUT | textInput输入内容发生变化时触发该事件。触发该事件的条件：输入内容发生变化时。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)。<br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)中包含1个参数：<br> <b>ArkUI_StringAsyncEvent.pStr</b>：输入的文本内容。  |
| NODE_TEXT_INPUT_ON_SUBMIT | textInput按下输入法回车键触发该事件。触发该事件的条件：按下输入法回车键。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>：输入法回车键类型。  |
| NODE_TEXT_INPUT_ON_CUT | 长按输入框内部区域弹出剪贴板后，点击剪切板剪切按钮，触发该回调。触发该事件的条件：长按输入框内部区域弹出剪贴板后，点击剪切板剪切按钮。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)。<br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)中包含1个参数：<br> <b>ArkUI_StringAsyncEvent.pStr</b>：剪切的文本内容。   |
| NODE_TEXT_INPUT_ON_PASTE | 长按输入框内部区域弹出剪贴板后，点击剪切板粘贴按钮，触发该回调。触发该事件的条件：长按输入框内部区域弹出剪贴板后，点击剪切板粘贴按钮。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)。<br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)中包含1个参数：<br> <b>ArkUI_StringAsyncEvent.pStr</b>：粘贴的文本内容。   |
| NODE_TEXT_INPUT_ON_TEXT_SELECTION_CHANGE | 文本选择的位置发生变化时，触发该回调。触发该事件的条件：文本选择的位置发生变化时。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>：表示所选文本的起始位置。<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>：表示所选文本的结束位置。  |
| NODE_TEXT_INPUT_ON_EDIT_CHANGE | 输入状态变化时，触发该回调。触发该事件的条件：输入状态变化时。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>：表示true表示正在输入。   |
| NODE_TEXT_INPUT_ON_INPUT_FILTER_ERROR | 设置NODE_TEXT_INPUT_INPUT_FILTER，正则匹配失败时触发。触发该事件的条件：正则匹配失败时。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)。<br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)中包含1个参数：<br> <b>ArkUI_StringAsyncEvent.pStr</b>：表示正则匹配失败时，被过滤的内容。 |
| NODE_TEXT_INPUT_ON_CONTENT_SCROLL | 文本内容滚动时，触发该回调。触发该事件的条件：文本内容滚动时。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>：表示文本在内容区的横坐标偏移。<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>：表示文本在内容区的纵坐标偏移。  |
| NODE_TEXT_INPUT_ON_CONTENT_SIZE_CHANGE | textInput输入内容发生变化时触发该事件。触发该事件的条件：输入内容发生变化时。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>：表示文本的宽度。<br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>：表示文本的高度。  |
| NODE_TEXT_INPUT_ON_WILL_INSERT = 7009 | 定义在将要输入时，触发回调的枚举值。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)。<br> 通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为0的value.f32：插入的值的位置信息。<br> 通过OH_ArkUI_NodeEvent_GetStringValue获取到index为0的buffer字符串：插入的值。  |
| NODE_TEXT_INPUT_ON_DID_INSERT = 7010 | 定义在输入完成时，触发回调的枚举值。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)。<br> 通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为0的value.f32：插入的值的位置信息。<br> 通过OH_ArkUI_NodeEvent_GetStringValue获取到index为0的buffer字符串：插入的值。  |
| NODE_TEXT_INPUT_ON_WILL_DELETE = 7011 | 定义在将要删除时，触发回调的枚举值。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)。<br> 通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为0的value.f32：删除的值的位置信息。<br> 通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为1的value.i32：删除值的方向，0为向后删除，1为向前删除。<br> 通过OH_ArkUI_NodeEvent_GetStringValue获取到index为0的buffer字符串：删除的值。   |
| NODE_TEXT_INPUT_ON_DID_DELETE = 7012 | 定义在删除完成时，触发回调的枚举值。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)。<br> 通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为0的value.f32：删除的值的位置信息。<br> 通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为1的value.i32：删除值的方向，0为向后删除，1为向前删除。<br> 通过OH_ArkUI_NodeEvent_GetStringValue获取到index为0的buffer字符串：删除的值。  |
| NODE_TEXT_INPUT_ON_CHANGE_WITH_PREVIEW_TEXT = 7013 | 定义textInput组件在内容改变时（包含预上屏内容），触发回调的枚举值。事件回调发生时，联合类型[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)为[ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md)。<br> [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md)包含参数：<br> <b>ArkUI_TextChangeEvent.pStr</b>: textInput的内容。<b>ArkUI_TextChangeEvent.pExtendStr</b>: textInput的预上屏内容。<b>ArkUI_TextChangeEvent.number</b>: textInput的预上屏起始位置。<br>**起始版本：** 15    |
| NODE_TEXT_INPUT_ON_WILL_CHANGE = 7014 | 定义TextInput组件在内容将要改变时（包含预上屏内容），触发回调的枚举值。事件回调发生时，联合类型[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)为[ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md)。<br> [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md)包含参数：<br> <b>ArkUI_TextChangeEvent.pStr</b>：TextInput的内容。<b>ArkUI_TextChangeEvent.pExtendStr</b>：TextInput的预上屏内容。<b>ArkUI_TextChangeEvent.number</b>：TextInput的预上屏起始位置。<br>**起始版本：** 20   |
| NODE_TEXT_AREA_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_AREA | 输入内容发生变化时，触发该回调。触发该事件的条件：输入内容发生变化时。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)。<br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)中包含1个参数：<br> <b>ArkUI_StringAsyncEvent.pStr</b>：当前输入的文本内容。 |
| NODE_TEXT_AREA_ON_PASTE | 长按输入框内部区域弹出剪贴板后，点击剪切板粘贴按钮，触发该回调。触发该事件的条件：长按输入框内部区域弹出剪贴板后，点击剪切板粘贴按钮。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)。<br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)中包含1个参数：<br> <b>ArkUI_StringAsyncEvent.pStr</b>：粘贴的文本内容。  |
| NODE_TEXT_AREA_ON_TEXT_SELECTION_CHANGE | 文本选择的位置发生变化时，触发该回调。触发该事件的条件：文本选择的位置发生变化时。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>：表示所选文本的起始位置。<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>：表示所选文本的结束位置。 |
| NODE_TEXT_AREA_ON_EDIT_CHANGE | 输入状态变化时，触发该回调。触发该事件的条件：输入状态变化时。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>：表示true表示正在输入。  |
| NODE_TEXT_AREA_ON_SUBMIT | textArea按下输入法回车键触发该事件。触发该事件的条件：按下输入法回车键。keyType为ARKUI_ENTER_KEY_TYPE_NEW_LINE时不触发<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>：输入法回车键类型。  |
| NODE_TEXT_AREA_ON_INPUT_FILTER_ERROR | 设置NODE_TEXT_AREA_INPUT_FILTER，正则匹配失败时触发。触发该事件的条件：正则匹配失败时。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)。<br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)中包含1个参数：<br> <b>ArkUI_StringAsyncEvent.pStr</b>：表示正则匹配失败时，被过滤的内容。 |
| NODE_TEXT_AREA_ON_CONTENT_SCROLL | 文本内容滚动时，触发该回调。触发该事件的条件：文本内容滚动时。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>：表示文本在内容区的横坐标偏移。<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>：表示文本在内容区的纵坐标偏移。  |
| NODE_TEXT_AREA_ON_CONTENT_SIZE_CHANGE | textArea输入内容发生变化时触发该事件。触发该事件的条件：输入内容发生变化时。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>：表示文本的宽度。<br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>：表示文本的高度。 |
| NODE_TEXT_AREA_ON_WILL_INSERT = 8008 | 定义在将要输入时，触发回调的枚举值。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)。<br> 通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为0的value.f32：插入的值的位置信息。<br> 通过OH_ArkUI_NodeEvent_GetStringValue获取到index为0的buffer字符串：插入的值。  |
| NODE_TEXT_AREA_ON_DID_INSERT = 8009 | 定义在输入完成时，触发回调的枚举值。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)。<br> 通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为0的value.f32：插入的值的位置信息。<br> 通过OH_ArkUI_NodeEvent_GetStringValue获取到index为0的buffer字符串：插入的值。   |
| NODE_TEXT_AREA_ON_WILL_DELETE = 8010 | 定义在将要删除时，触发回调的枚举值。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)。<br> 通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为0的value.f32：删除的值的位置信息。<br> 通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为1的value.i32：删除值的方向，0为向后删除，1为向前删除。<br> 通过OH_ArkUI_NodeEvent_GetStringValue获取到index为0的buffer字符串：删除的值。  |
| NODE_TEXT_AREA_ON_DID_DELETE = 8011 | 定义在删除完成时，触发回调的枚举值。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)。<br> 通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为0的value.f32：删除的值的位置信息。<br> 通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为1的value.i32：删除值的方向，0为向后删除，1为向前删除。<br> 通过OH_ArkUI_NodeEvent_GetStringValue获取到index为0的buffer字符串：删除的值。 |
| NODE_TEXT_AREA_ON_CHANGE_WITH_PREVIEW_TEXT = 8012 | 定义textArea组件在内容改变时（包含预上屏内容），触发回调的枚举值。事件回调发生时，联合类型[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)为[ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md)。<br> [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md)包含参数：<br> <b>ArkUI_TextChangeEvent.pStr</b>: textArea的内容。<b>ArkUI_TextChangeEvent.pExtendStr</b>: textArea的预上屏内容。<b>ArkUI_TextChangeEvent.number</b>: textArea的预上屏起始位置。<br>**起始版本：** 15  |
| NODE_TEXT_AREA_ON_WILL_CHANGE = 8013 | 定义TextArea组件在内容将要改变时（包含预上屏内容），触发回调的枚举值。事件回调发生时，联合类型[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)为[ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md)。<br> [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md)包含参数：<br> <b>ArkUI_TextChangeEvent.pStr</b>：TextArea的内容。<b>ArkUI_TextChangeEvent.pExtendStr</b>：TextArea的预上屏内容。<b>ArkUI_TextChangeEvent.number</b>：TextArea的预上屏起始位置。<br>**起始版本：** 20    |
| NODE_CHECKBOX_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CHECKBOX | 定义ARKUI_NODE_CHECKBOX当选中状态发生变化时，触发该回调。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>1:表示已选中, 0: 表示未选中。   |
| NODE_DATE_PICKER_EVENT_ON_DATE_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_DATE_PICKER | 定义ARKUI_NODE_DATE_PICKER列表组件的滚动触摸事件枚举值。触发该事件的条件：选择日期时触发该事件。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含3个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>：表示选中时间的年。<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>：表示选中时间的月，取值范围：[0-11]。<br> <b>ArkUI_NodeComponentEvent.data[2].i32</b>：表示选中时间的天。   |
| NODE_TIME_PICKER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TIME_PICKER | 定义ARKUI_NODE_TIME_PICKER列表组件的滚动触摸事件枚举值。触发该事件的条件：选择时间时触发该事件。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>：表示选中时间的时，取值范围：[0-23]。<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>：表示选中时间的分，取值范围：[0-59]。   |
| NODE_TEXT_PICKER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_PICKER | 定义ARKUI_NODE_TEXT_PICKER列表组件的滚动触摸事件枚举值。触发该事件的条件 ：选择文本时触发该事件。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数：<br> <b>ArkUI_NodeComponentEvent.data[0...11].i32</b>表示选中数据的维度。|
| NODE_TEXT_PICKER_EVENT_ON_SCROLL_STOP = 15001 | 定义ARKUI_NODE_TEXT_PICKER列表组件的滚动触摸事件枚举值。触发该事件的条件 ：滑动选择文本项停止时触发该事件。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数：<br> <b>ArkUI_NodeComponentEvent.data[0...11].i32</b>表示选中数据的维度。<br>**起始版本：** 14 |
| NODE_CALENDAR_PICKER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CALENDAR_PICKER | 定义NODE_CALENDAR_PICKER选中日期时触发的事件。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> <b>ArkUI_NodeComponent.data[0].u32</b>选中的年。<br> <b>ArkUI_NodeComponent.data[1].u32</b>选中的月。<br> <b>ArkUI_NodeComponent.data[2].u32</b>选中的日。 |
| NODE_SLIDER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SLIDER | 定义ARKUI_NODE_SLIDER拖动或点击时触发事件回调。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>：当前滑动进度值。<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>：事件触发的相关状态值  |
| NODE_RADIO_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_RADIO | 定义ARKUI_NODE_RADIO拖动或点击时触发事件回调。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>：单选框的状态。  |
| NODE_IMAGE_ANIMATOR_EVENT_ON_START = MAX_NODE_SCOPE_NUM * ARKUI_NODE_IMAGE_ANIMATOR | 定义帧动画开始的状态回调。触发该事件的条件：<br> 1、帧动画开始播放时。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中不包含参数。  |
| NODE_IMAGE_ANIMATOR_EVENT_ON_PAUSE | 定义帧动画播放暂停时的状态回调。触发该事件的条件：<br> 1、帧动画暂停播放时。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中不包含参数。 |
| NODE_IMAGE_ANIMATOR_EVENT_ON_REPEAT | 定义帧动画c重复播放时的状态回调。触发该事件的条件：<br> 1、帧动画重复播放时。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中不包含参数。  |
| NODE_IMAGE_ANIMATOR_EVENT_ON_CANCEL | 定义帧动画返回最初状态时的状态回调。触发该事件的条件：<br> 1、帧动画返回最初状态时。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中不包含参数。 |
| NODE_IMAGE_ANIMATOR_EVENT_ON_FINISH | 定义帧动画播放完成时或者停止播放时的状态回调。触发该事件的条件：<br> 1、帧动画播放完成时或停止播放时。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中不包含参数。  |
| NODE_CHECKBOX_GROUP_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CHECKBOX_GROUP | 定义ARKUI_NODE_CHECKBOX_GROUP的选中状态或群组内的Checkbox的选中状态发生变化时，触发该回调。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)。<br> <b>ArkUI_StringAsyncEvent.pStr</b>Name: 被选中的checkbox的名字;Status:0: 表示群组多选择框全部选择。1: 群组多选择框部分选择。2: 群组多选择框全部没有选择。<br>**起始版本：** 15   |
| NODE_SWIPER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SWIPER | 定义ARKUI_NODE_SWIPER当前元素索引变化时触发事件回调。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>：表示当前显示元素的索引。  |
| NODE_SWIPER_EVENT_ON_ANIMATION_START | 定义ARKUI_NODE_SWIPER切换动画开始时触发回调。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含5个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>：表示当前显示元素的索引。<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>：表示切换动画目标元素的索引。<br> <b>ArkUI_NodeComponentEvent.data[2].f32</b>：表示主轴方向上当前显示元素相对Swiper起始位置的位移。<br> <b>ArkUI_NodeComponentEvent.data[3].f32</b>：表示主轴方向上目标元素相对Swiper起始位置的位移。<br> <b>ArkUI_NodeComponentEvent.data[4].f32</b>：表示离手速度。  |
| NODE_SWIPER_EVENT_ON_ANIMATION_END | 定义ARKUI_NODE_SWIPER切换动画结束是触发回调。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>：表示当前显示元素的索引。<br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>：表示主轴方向上当前显示元素相对Swiper起始位置的位移。  |
| NODE_SWIPER_EVENT_ON_GESTURE_SWIPE | 定义ARKUI_NODE_SWIPER在页面跟手滑动过程中，逐帧触发该回调。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>：表示当前显示元素的索引。<br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>：表示主轴方向上当前显示元素相对Swiper起始位置的位移。 |
| NODE_SWIPER_EVENT_ON_CONTENT_DID_SCROLL | 定义ARKUI_NODE_SWIPER监听Swiper页面滑动事件。使用说明 ：<br> 1、设置{@link ArkUI_SwiperDisplayModeType}属性为ARKUI_SWIPER_DISPLAY_MODE_AUTO_LINEAR时，该接口不生效。<br> 2、循环场景下，设置prevMargin和nextMargin属性，使得Swiper前后端显示同一页面时，该接口不生效。<br> 3、在页面滑动过程中，会对视窗内所有页面逐帧触发ContentDidScrollCallback回调。<br> 例如，当视窗内有下标为0、1的两个页面时，会每帧触发两次index值分别为0和1的回调。<br> 4、设置displayCount属性的swipeByGroup参数为true时，若同组中至少有一个页面在视窗内时，<br> 则会对同组中所有页面触发回调。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含4个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>：Swiper组件的索引，和onChange事件中的index值变化保持一致。<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>：视窗内某个页面的索引。<br> <b>ArkUI_NodeComponentEvent.data[2].f32</b>：页面相对于Swiper主轴起始位置（selectedIndex对应页面的起始位置）的移动比例。<br> <b>ArkUI_NodeComponentEvent.data[3].f32</b>：主轴方向上页面的长度。   |
| NODE_SWIPER_EVENT_ON_SELECTED = 1001005 | 定义当ARKUI_NODE_SWIPER选中元素改变时触发回调。触发该事件的条件：<br> 1、滑动离手时满足翻页阈值，开始切换动画时。<br> 2、通过NODE_SWIPER_INDEX或NODE_SWIPER_SWIPE_TO_INDEX切换页面时。<br> 事件回调发生时, 事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) 中包含1个参数:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: 表示当前选中元素的索引。<br>**起始版本：** 18    |
| NODE_SWIPER_EVENT_ON_UNSELECTED = 1001006 | 定义当ARKUI_NODE_SWIPER页面切换事件回调。满足以下任一条件，即可触发该事件：<br> 1. 滑动离手时满足翻页阈值，并且开始切换动画。<br> 2. 通过NODE_SWIPER_INDEX或NODE_SWIPER_SWIPE_TO_INDEX切换页面。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) 中包含1个参数:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: 表示将要隐藏元素的索引。<br>**起始版本：** 18    |
| NODE_SWIPER_EVENT_ON_CONTENT_WILL_SCROLL = 1001007 | 定义ARKUI_NODE_SWIPER滑动行为拦截事件。使用说明: 在页面滑动前, </b>ContentWillScrollCallback</b> 回调会触发。<br> 事件回调发生时， 事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含3个参数:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: 当前显示元素的索引。<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: 切换动画目标元素的索引。<br> <b>ArkUI_NodeComponentEvent.data[2].f32</b>: 每帧的滑动偏移量。正数表示向后滑动（例如从index=1到index=0），负数表示向前滑动（例如从index=0到index=1）。<br>**起始版本：** 15   |
| NODE_SWIPER_EVENT_ON_SCROLL_STATE_CHANGED = 1001008 | 定义ARKUI_NODE_SWIPER滑动状态变化事件。触发该事件的条件 ：<br> Swiper在跟手滑动、离手动画、停止三种滑动状态变化时触发。事件回调发生时， 事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: 当前滑动状态，参数类型[ArkUI_ScrollState](capi-native-type-h.md#arkui_scrollstate)。<br>**起始版本：** 20  |
| NODE_SCROLL_EVENT_ON_SCROLL = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SCROLL | 定义滚动容器组件的滚动事件枚举值。触发该事件的条件 ：<br> 1、滚动组件触发滚动时触发，支持键鼠操作等其他触发滚动的输入设置。<br> 2、通过滚动控制器API接口调用。<br> 3、越界回弹。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>：表示距离上一次事件触发的X轴增量。<br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>：表示距离上一次事件触发的Y轴增量。  |
| NODE_SCROLL_EVENT_ON_SCROLL_FRAME_BEGIN | 定义滚动容器组件的滚动帧始事件枚举值。触发该事件的条件 ：<br> 1、滚动组件触发滚动时触发，包括键鼠操作等其他触发滚动的输入设置。<br> 2、调用控制器接口时不触发。<br> 3、越界回弹不触发。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>：表示即将发生的滚动量。<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>：表示当前滚动状态。<br> <b>::ArkUI_NodeComponentEvent</b>中包含1个返回值：<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>：事件处理函数中可根据应用场景计算实际需要的滚动量并存于data[0].f32中，Scroll将按照返回值的实际滚动量进行滚动。 |
| NODE_SCROLL_EVENT_ON_WILL_SCROLL | 定义滚动容器组件的滑动前触发事件枚举值。触发该事件的条件 ：<br> 1、滚动组件触发滚动时触发，支持键鼠操作等其他触发滚动的输入设置。<br> 2、通过滚动控制器API接口调用。<br> 3、越界回弹。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含4个参数: <br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>:每帧滚动的偏移量，内容向左滚动时偏移量为正，向右滚动时偏移量为负，单位vp。 <br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>:每帧滚动的偏移量，内容向上滚动时偏移量为正，向下滚动时偏移量为负，单位vp。 <br> <b>ArkUI_NodeComponentEvent.data[2].i32</b>: 当前滑动状态，参数类型[ArkUI_ScrollState](capi-native-type-h.md#arkui_scrollstate)。<br> <b>ArkUI_NodeComponentEvent.data[3].i32</b>: 当前滚动的来源，参数类型[ArkUI_ScrollSource](capi-native-type-h.md#arkui_scrollsource)。  |
| NODE_SCROLL_EVENT_ON_DID_SCROLL | 定义滚动容器组件的滑动时触发事件枚举值。触发该事件的条件 ：<br> 1、滚动组件触发滚动时触发，支持键鼠操作等其他触发滚动的输入设置。<br> 2、通过滚动控制器API接口调用。<br> 3、越界回弹。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含3个参数: <br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>:每帧滚动的偏移量，内容向左滚动时偏移量为正，向右滚动时偏移量为负，单位vp。 <br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>:每帧滚动的偏移量，内容向上滚动时偏移量为正，向下滚动时偏移量为负，单位vp。 <br> <b>ArkUI_NodeComponentEvent.data[2].i32</b>: 当前滑动状态，参数类型[ArkUI_ScrollState](capi-native-type-h.md#arkui_scrollstate)。  |
| NODE_SCROLL_EVENT_ON_SCROLL_START | 定义滚动容器组件的滚动开始事件枚举值。触发该事件的条件 ：<br> 1、滚动组件开始滚动时触发，支持键鼠操作等其他触发滚动的输入设置。<br> 2、通过滚动控制器API接口调用后开始，带过渡动效。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中不包含参数。  |
| NODE_SCROLL_EVENT_ON_SCROLL_STOP | 定义滚动容器组件的滚动停止事件枚举值。触发该事件的条件 ：<br> 1、滚动组件触发滚动后停止，支持键鼠操作等其他触发滚动的输入设置。<br> 2、通过滚动控制器API接口调用后停止，带过渡动效。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中不包含参数。   |
| NODE_SCROLL_EVENT_ON_SCROLL_EDGE | 定义滚动容器组件的滚动边缘事件枚举值。触发该事件的条件 ：<br> 1、滚动组件滚动到边缘时触发，支持键鼠操作等其他触发滚动的输入设置。<br> 2、通过滚动控制器API接口调用。<br> 3、越界回弹。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数。<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>表示当前碰到的是上下左右哪个边。 |
| NODE_SCROLL_EVENT_ON_REACH_START | 定义滚动容器组件到达起始位置时触发回调。触发该事件的条件 ：<br> 1、组件到达起始位置时触发。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中不包含参数。 |
| NODE_SCROLL_EVENT_ON_REACH_END | 定义滚动容器组件到底末尾位置时触发回调。触发该事件的条件 ：<br> 1、组件到底末尾位置时触发。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中不包含参数。   |
| NODE_SCROLL_EVENT_ON_WILL_STOP_DRAGGING | 定义滚动容器组件拖划即将离手回调。触发该事件的条件： <br> 滚动容器组件拖划即将离手时触发。 <br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。 <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数: <br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: 划动离手速度，单位vp/s。 <br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>: 预计滚动停止位置。  |
| NODE_SCROLL_EVENT_ON_DID_ZOOM | 定义Scroll组件缩放回调。触发该事件的条件：Scroll组件缩放每帧完成时触发。 <br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。 <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数: <br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: 当前缩放比例。 <br>**起始版本：** 20  |
| NODE_SCROLL_EVENT_ON_ZOOM_START | 定义Scroll组件缩放开始回调。触发该事件的条件：Scroll组件缩放开始时触发。 <br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。 <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中不包含参数。<br>**起始版本：** 20    |
| NODE_SCROLL_EVENT_ON_ZOOM_STOP | 定义Scroll组件缩放停止回调。触发该事件的条件：Scroll组件缩放停止时触发。 <br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。 <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中不包含参数。<br>**起始版本：** 20    |
| NODE_LIST_ON_SCROLL_INDEX = MAX_NODE_SCOPE_NUM * ARKUI_NODE_LIST | 定义ARKUI_NODE_LIST有子组件划入或划出List显示区域时触发事件枚举值。触发该事件的条件 ：<br> 列表初始化时会触发一次，List显示区域内第一个子组件的索引值或最后一个子组件的索引值有变化时会触发。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含3个参数: <br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: List显示区域内第一个子组件的索引值. <br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: List显示区域内最后一个子组件的索引值. <br> <b>ArkUI_NodeComponentEvent.data[2].i32</b>: List显示区域内中间位置子组件的索引值.  |
| NODE_LIST_ON_WILL_SCROLL | 定义ARKUI_NODE_LIST组件的滑动前触发事件枚举值。触发该事件的条件 ：<br> 1、滚动组件触发滚动时触发，支持键鼠操作等其他触发滚动的输入设置。<br> 2、通过滚动控制器API接口调用。<br> 3、越界回弹。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含3个参数: <br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>:每帧滚动的偏移量，list内容向上滚动时偏移量为正，向下滚动时偏移量为负。 <br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: 当前滑动状态，参数类型[ArkUI_ScrollState](capi-native-type-h.md#arkui_scrollstate)。<br> <b>ArkUI_NodeComponentEvent.data[2].i32</b>: 当前滚动的来源，参数类型[ArkUI_ScrollSource](capi-native-type-h.md#arkui_scrollsource)。 |
| NODE_LIST_ON_DID_SCROLL | 定义ARKUI_NODE_LIST组件的滑动时触发事件枚举值。触发该事件的条件 ：<br> 1、滚动组件触发滚动时触发，支持键鼠操作等其他触发滚动的输入设置。<br> 2、通过滚动控制器API接口调用。<br> 3、越界回弹。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数: <br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>:每帧滚动的偏移量，list内容向上滚动时偏移量为正，向下滚动时偏移量为负。 <br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: 当前滑动状态。  |
| NODE_LIST_ON_SCROLL_VISIBLE_CONTENT_CHANGE | 定义ARKUI_NODE_LIST当前显示内容发生改变的时候触发事件枚举值。触发该事件的条件 ：<br> 列表初始化时会触发一次，List显示区域内第一个子组件的索引值或最后一个子组件的索引值有变化时会触发。计算触发条件时，每一个ListItem、ListItemGroup中的header或footer都算一个子组件。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含3个参数: <br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: List显示区域内第一个子组件的索引值。 <br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: List显示区域起始端在ListItemGroup中的区域。类型为[ArkUI_ListItemGroupArea](capi-native-type-h.md#arkui_listitemgrouparea)。<br> <b>ArkUI_NodeComponentEvent.data[2].i32</b>: List显示区域起始端在ListItemGroup中的ListItem索引号，如果List显示区域起始端不在ListItem上，该值为-1。 <br> <b>ArkUI_NodeComponentEvent.data[4].i32</b>: List显示区域内最后一个子组件的索引值。 <br> <b>ArkUI_NodeComponentEvent.data[5].i32</b>: List显示区域末尾端在ListItemGroup中的区域。类型为[ArkUI_ListItemGroupArea](capi-native-type-h.md#arkui_listitemgrouparea)。<br> <b>ArkUI_NodeComponentEvent.data[6].i32</b>: List显示区域末尾端在ListItemGroup中的ListItem索引号，如果List显示区域末尾端不在ListItem上，该值为-1。 <br>**起始版本：** 15     |
| NODE_REFRESH_STATE_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_REFRESH | 定义ARKUI_NODE_REFRESH刷新状态变更触发该事件。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>：刷新状态。   |
| NODE_REFRESH_ON_REFRESH | 定义ARKUI_NODE_REFRESH进入刷新状态时触发该事件。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中不包含参数：  |
| NODE_REFRESH_ON_OFFSET_CHANGE | 定义ARKUI_NODE_REFRESH下拉距离发生变化时触发该事件。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>：下拉距离。   |
| NODE_ON_WILL_SCROLL = MAX_NODE_SCOPE_NUM * ARKUI_NODE_WATER_FLOW | 定义ARKUI_NODE_WATER_FLOW组件的滑动前触发事件枚举值。触发该事件的条件 ：<br> 1、滚动组件触发滚动时触发，支持键鼠操作等其他触发滚动的输入设置。<br> 2、通过滚动控制器API接口调用。<br> 3、越界回弹。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含3个参数: <br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: 每帧滚动的偏移量，内容向上滚动时偏移量为正，向下滚动时偏移量为负。 <br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: 当前滑动状态，参数类型[ArkUI_ScrollState](capi-native-type-h.md#arkui_scrollstate)。<br> <b>ArkUI_NodeComponentEvent.data[2].i32</b>: 当前滚动的来源，参数类型[ArkUI_ScrollSource](capi-native-type-h.md#arkui_scrollsource)。  |
| NODE_WATER_FLOW_ON_DID_SCROLL | 定义ARKUI_NODE_WATER_FLOW组件的滑动时触发事件枚举值。触发该事件的条件 ：<br> 1、滚动组件触发滚动时触发，支持键鼠操作等其他触发滚动的输入设置。<br> 2、通过滚动控制器API接口调用。<br> 3、越界回弹。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数: <br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: 每帧滚动的偏移量，内容向上滚动时偏移量为正，向下滚动时偏移量为负。 <br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: 当前滑动状态。  |
| NODE_WATER_FLOW_ON_SCROLL_INDEX | 定义ARKUI_NODE_WATER_FLOW当前瀑布流显示的起始位置/终止位置的子组件发生变化时触发事件枚举值。触发该事件的条件 ：<br> 瀑布流显示区域上第一个子组件/最后一个组件的索引值有变化就会触发。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含3个参数: <br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: 当前显示的WaterFlow起始位置的索引值。 <br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: 当前显示的瀑布流终止位置的索引值。 |

### ArkUI_NodeDirtyFlag

```
enum ArkUI_NodeDirtyFlag
```

**描述：**


自定义组件调用<b>::markDirty</b>是传递的脏区标识类型。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| NODE_NEED_MEASURE = 1 | 重新测算大小。该flag类型触发时，同时也默认会触发重新布局。 |
| NODE_NEED_LAYOUT | 重新布局位置。 |
| NODE_NEED_RENDER | 重新进行绘制。 |

### ArkUI_NodeCustomEventType

```
enum ArkUI_NodeCustomEventType
```

**描述：**


定义自定义组件事件类型。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_NODE_CUSTOM_EVENT_ON_MEASURE = 1 << 0 | measure 类型。 |
| ARKUI_NODE_CUSTOM_EVENT_ON_LAYOUT = 1 << 1 | layout 类型。 |
| ARKUI_NODE_CUSTOM_EVENT_ON_DRAW = 1 << 2 | draw 类型。 |
| ARKUI_NODE_CUSTOM_EVENT_ON_FOREGROUND_DRAW = 1 << 3 | foreground 类型。 |
| ARKUI_NODE_CUSTOM_EVENT_ON_OVERLAY_DRAW = 1 << 4 | overlay 类型。 |
| ARKUI_NODE_CUSTOM_EVENT_ON_DRAW_FRONT = 1 << 5 |  |
| ARKUI_NODE_CUSTOM_EVENT_ON_DRAW_BEHIND = 1 << 6 |  |

### ArkUI_NodeAdapterEventType

```
enum ArkUI_NodeAdapterEventType
```

**描述：**


定义节点适配器事件枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| NODE_ADAPTER_EVENT_WILL_ATTACH_TO_NODE = 1 | 组件和adapter关联时产生该事件。 |
| NODE_ADAPTER_EVENT_WILL_DETACH_FROM_NODE = 2 | 组件和adapter取消关联时产生该事件。 |
| NODE_ADAPTER_EVENT_ON_GET_NODE_ID = 3 | Adapter需要添加新元素时获取新元素的唯一标识符时产生该事件。 |
| NODE_ADAPTER_EVENT_ON_ADD_NODE_TO_ADAPTER = 4 | Adapter需要添加新元素时获取新元素的内容时产生该事件。 |
| NODE_ADAPTER_EVENT_ON_REMOVE_NODE_FROM_ADAPTER = 5 | Adapter将元素移除时产生该事件。 |

### ArkUI_NodeContentEventType

```
enum ArkUI_NodeContentEventType
```

**描述：**


定义NodeContent事件类型。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| NODE_CONTENT_EVENT_ON_ATTACH_TO_WINDOW = 0 | 上树事件。 |
| NODE_CONTENT_EVENT_ON_DETACH_FROM_WINDOW = 1 | 下树事件。 |

### ArkUI_InspectorErrorCode

```
enum ArkUI_InspectorErrorCode
```

**描述：**


inspector错误码的枚举。

**起始版本：** 15

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_INSPECTOR_NATIVE_RESULT_SUCCESSFUL = 0 | 成功。 |
| ARKUI_INSPECTOR_NATIVE_RESULT_BAD_PARAMETER = -1 | 参数错误。 |


## 函数说明

### OH_ArkUI_NodeEvent_GetEventType()

```
ArkUI_NodeEventType OH_ArkUI_NodeEvent_GetEventType(ArkUI_NodeEvent* event)
```

**描述：**


获取组件事件类型。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | 组件事件指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeEventType](capi-native-node-h.md#arkui_nodeeventtype) | ArkUI_NodeEventType 组件事件类型。 |

### OH_ArkUI_NodeEvent_GetTargetId()

```
int32_t OH_ArkUI_NodeEvent_GetTargetId(ArkUI_NodeEvent* event)
```

**描述：**


获取事件自定义标识ID。该事件id在调用[registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent)函数时作为参数传递进来，可应用于同一事件入口函数[registerNodeEventReceiver](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeeventreceiver)分发逻辑。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | 组件事件指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | int32_t 事件自定义标识ID。 |

### OH_ArkUI_NodeEvent_GetNodeHandle()

```
ArkUI_NodeHandle OH_ArkUI_NodeEvent_GetNodeHandle(ArkUI_NodeEvent* event)
```

**描述：**


获取触发该事件的组件对象。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | 组件事件指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | ArkUI_NodeHandle 触发该组件的组件对象。 |

### OH_ArkUI_NodeEvent_GetInputEvent()

```
ArkUI_UIInputEvent* OH_ArkUI_NodeEvent_GetInputEvent(ArkUI_NodeEvent* event)
```

**描述：**


获取组件事件中的输入事件（如触碰事件）数据。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | 组件事件指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_UIInputEvent* | ArkUI_UIInputEvent 输入事件数据指针。 |

### OH_ArkUI_NodeEvent_GetNodeComponentEvent()

```
ArkUI_NodeComponentEvent* OH_ArkUI_NodeEvent_GetNodeComponentEvent(ArkUI_NodeEvent* event)
```

**描述：**


获取组件事件中的数字类型数据。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | 组件事件指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_NodeComponentEvent* | ArkUI_NodeComponentEvent 数字类型数据指针。 |

### OH_ArkUI_NodeEvent_GetStringAsyncEvent()

```
ArkUI_StringAsyncEvent* OH_ArkUI_NodeEvent_GetStringAsyncEvent(ArkUI_NodeEvent* event)
```

**描述：**


获取组件事件中的字符串数据。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | 组件事件指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_StringAsyncEvent* | ArkUI_StringAsyncEvent 字符串数据指针。 |

### OH_ArkUI_NodeEvent_GetTextChangeEvent()

```
ArkUI_TextChangeEvent* OH_ArkUI_NodeEvent_GetTextChangeEvent(ArkUI_NodeEvent* event)
```

**描述：**


获取组件事件中的ArkUI_TextChangeEvent数据。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | 组件事件指针，不应为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_TextChangeEvent* | 返回ArkUI_TextChangeEvent对象的指针。 |

### OH_ArkUI_NodeEvent_GetUserData()

```
void* OH_ArkUI_NodeEvent_GetUserData(ArkUI_NodeEvent* event)
```

**描述：**


获取组件事件中的用户自定义数据。该自定义参数在调用[registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent)函数时作为参数传递进来，可应用于事件触发时的业务逻辑处理。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | 组件事件指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| void* | void 用户自定义数据指针。 |

### OH_ArkUI_NodeEvent_GetNumberValue()

```
int32_t OH_ArkUI_NodeEvent_GetNumberValue(ArkUI_NodeEvent* event, int32_t index, ArkUI_NumberValue* value)
```

**描述：**


获取组件回调事件的数字类型参数。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | 组件事件指针。 |
| int32_t index | 返回值索引。 |
| [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)* value | 具体返回值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INDEX_OUT_OF_RANGE](capi-native-type-h.md#arkui_errorcode) 组件事件中参数长度超限。<br>         [ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 组件事件中不存在该数据。 |

### OH_ArkUI_NodeEvent_GetStringValue()

```
int32_t OH_ArkUI_NodeEvent_GetStringValue(ArkUI_NodeEvent* event, int32_t index, char** string, int32_t* stringSize)
```

**描述：**


获取组件回调事件的字符串类型参数，字符串数据仅在事件回调过程中有效，需要在事件回调外使用建议进行额外拷贝处理。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | 组件事件指针。 |
| int32_t index | 返回值索引。 |
| char** string | 字符串数组的指针。 |
| int32_t* stringSize | 字符串数组的长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INDEX_OUT_OF_RANGE](capi-native-type-h.md#arkui_errorcode) 组件事件中参数长度超限。<br>         [ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 组件事件中不存在该数据。 |

### OH_ArkUI_NodeEvent_SetReturnNumberValue()

```
int32_t OH_ArkUI_NodeEvent_SetReturnNumberValue(ArkUI_NodeEvent* event, ArkUI_NumberValue* value, int32_t size)
```

**描述：**


设置组件回调事件的返回值。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | 组件事件指针。 |
| [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)* value | 事件数字类型数组。 |
| int32_t size | 数组长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_NODE_EVENT_NO_RETURN](capi-native-type-h.md#arkui_errorcode) 组件事件不支持返回值。<br>         [ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 组件事件中不存在该数据。 |

### OH_ArkUI_NodeAdapter_Create()

```
ArkUI_NodeAdapterHandle OH_ArkUI_NodeAdapter_Create()
```

**描述：**


创建组件适配器对象。

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) | 组件适配器对象。 |

### OH_ArkUI_NodeAdapter_Dispose()

```
void OH_ArkUI_NodeAdapter_Dispose(ArkUI_NodeAdapterHandle handle)
```

**描述：**


销毁组件适配器对象。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | 组件适配器对象。 |

### OH_ArkUI_NodeAdapter_SetTotalNodeCount()

```
int32_t OH_ArkUI_NodeAdapter_SetTotalNodeCount(ArkUI_NodeAdapterHandle handle, uint32_t size)
```

**描述：**


设置Adapter中的元素总数。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | 组件适配器对象。 |
| uint32_t size | 元素数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>        [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>        [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeAdapter_GetTotalNodeCount()

```
uint32_t OH_ArkUI_NodeAdapter_GetTotalNodeCount(ArkUI_NodeAdapterHandle handle)
```

**描述：**


获取Adapter中的元素总数。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | 组件适配器对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | Adapter中的元素总数。 |

### OH_ArkUI_NodeAdapter_RegisterEventReceiver()

```
int32_t OH_ArkUI_NodeAdapter_RegisterEventReceiver(
ArkUI_NodeAdapterHandle handle, void* userData, void (*receiver)(ArkUI_NodeAdapterEvent* event))
```

**描述：**


注册Adapter相关回调事件。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| handle | 组件适配器对象。 |
| userData | 自定义数据。 |
| receiver | 事件接收回调。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t  | 错误码。<br>        [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>        [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeAdapter_UnregisterEventReceiver()

```
void OH_ArkUI_NodeAdapter_UnregisterEventReceiver(ArkUI_NodeAdapterHandle handle)
```

**描述：**


注销Adapter相关回调事件。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | 组件适配器对象。 |

### OH_ArkUI_NodeAdapter_ReloadAllItems()

```
int32_t OH_ArkUI_NodeAdapter_ReloadAllItems(ArkUI_NodeAdapterHandle handle)
```

**描述：**


通知Adapter进行全量元素变化。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | 组件适配器对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>        [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>        [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeAdapter_ReloadItem()

```
int32_t OH_ArkUI_NodeAdapter_ReloadItem(
ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)
```

**描述：**


通知Adapter进行局部元素变化。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | 组件适配器对象。 |
| uint32_t startPosition | 元素变化起始位置。 |
| uint32_t itemCount | 元素变化数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>        [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>        [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。<br>        ERROR_CODE_NATIVE_IMPL_NODE_ADAPTER_NO_LISTENER_ERROR NodeAdapter需要添加监听器。 |

### OH_ArkUI_NodeAdapter_RemoveItem()

```
int32_t OH_ArkUI_NodeAdapter_RemoveItem(
ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)
```

**描述：**


通知Adapter进行局部元素删除。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | 组件适配器对象。 |
| uint32_t startPosition | 元素删除起始位置。 |
| uint32_t itemCount | 元素删除数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>        [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>        [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。<br>        ERROR_CODE_NATIVE_IMPL_NODE_ADAPTER_NO_LISTENER_ERROR NodeAdapter需要添加监听器。 |

### OH_ArkUI_NodeAdapter_InsertItem()

```
int32_t OH_ArkUI_NodeAdapter_InsertItem(
ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)
```

**描述：**


通知Adapter进行局部元素插入。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | 组件适配器对象。 |
| uint32_t startPosition | 元素插入起始位置。 |
| uint32_t itemCount | 元素插入数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>        [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>        [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。<br>        ERROR_CODE_NATIVE_IMPL_NODE_ADAPTER_NO_LISTENER_ERROR NodeAdapter需要添加监听器。 |

### OH_ArkUI_NodeAdapter_MoveItem()

```
int32_t OH_ArkUI_NodeAdapter_MoveItem(ArkUI_NodeAdapterHandle handle, uint32_t from, uint32_t to)
```

**描述：**


通知Adapter进行局部元素移位。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | 组件适配器对象。 |
| uint32_t from | 元素移位起始位置。 |
| uint32_t to | 元素移位结束位置。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>        [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>        [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。<br>        ERROR_CODE_NATIVE_IMPL_NODE_ADAPTER_NO_LISTENER_ERROR NodeAdapter需要添加监听器。 |

### OH_ArkUI_NodeAdapter_GetAllItems()

```
int32_t OH_ArkUI_NodeAdapter_GetAllItems(ArkUI_NodeAdapterHandle handle, ArkUI_NodeHandle** items, uint32_t* size)
```

**描述：**


获取存储在Adapter中的所有元素。接口调用会返回元素的数组对象指针，该指针指向的内存数据需要开发者手动释放。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | 组件适配器对象。 |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)** items | 适配器内节点数组。 |
| uint32_t* size | 元素数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>        [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>        [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。<br>        ERROR_CODE_NATIVE_IMPL_NODE_ADAPTER_NO_LISTENER_ERROR NodeAdapter需要添加监听器。 |

### OH_ArkUI_NodeAdapterEvent_GetUserData()

```
void* OH_ArkUI_NodeAdapterEvent_GetUserData(ArkUI_NodeAdapterEvent* event)
```

**描述：**


获取注册事件时传入的自定义数据。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | 适配器事件对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| void* | 用户自定义数据的指针。 |

### OH_ArkUI_NodeAdapterEvent_GetType()

```
ArkUI_NodeAdapterEventType OH_ArkUI_NodeAdapterEvent_GetType(ArkUI_NodeAdapterEvent* event)
```

**描述：**


获取事件类型。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | 适配器事件对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeAdapterEventType](capi-native-node-h.md#arkui_nodeadaptereventtype) | 事件类型。 |

### OH_ArkUI_NodeAdapterEvent_GetRemovedNode()

```
ArkUI_NodeHandle OH_ArkUI_NodeAdapterEvent_GetRemovedNode(ArkUI_NodeAdapterEvent* event)
```

**描述：**


获取需要销毁的事件中待销毁的元素。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | 适配器事件对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | 待销毁的元素。 |

### OH_ArkUI_NodeAdapterEvent_GetItemIndex()

```
uint32_t OH_ArkUI_NodeAdapterEvent_GetItemIndex(ArkUI_NodeAdapterEvent* event)
```

**描述：**


获取适配器事件时需要操作的元素序号。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | 适配器事件对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | 元素序号。 |

### OH_ArkUI_NodeAdapterEvent_GetHostNode()

```
ArkUI_NodeHandle OH_ArkUI_NodeAdapterEvent_GetHostNode(ArkUI_NodeAdapterEvent* event)
```

**描述：**


获取使用该适配器的滚动类容器节点。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | 适配器事件对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | 适配器的滚动类容器节点。 |

### OH_ArkUI_NodeAdapterEvent_SetItem()

```
int32_t OH_ArkUI_NodeAdapterEvent_SetItem(ArkUI_NodeAdapterEvent* event, ArkUI_NodeHandle node)
```

**描述：**


设置需要新增到Adapter中的组件。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | 适配器事件对象。 |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 待添加的组件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>        [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>        [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeAdapterEvent_SetNodeId()

```
int32_t OH_ArkUI_NodeAdapterEvent_SetNodeId(ArkUI_NodeAdapterEvent* event, int32_t id)
```

**描述：**


设置生成的组件标识。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | 适配器事件对象。 |
| int32_t id | 设置返回的组件标识。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>        [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>        [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeCustomEvent_GetLayoutConstraintInMeasure()

```
ArkUI_LayoutConstraint* OH_ArkUI_NodeCustomEvent_GetLayoutConstraintInMeasure(ArkUI_NodeCustomEvent* event)
```

**描述：**


通过自定义组件事件获取测算过程中的约束尺寸。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | 自定义组件事件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_LayoutConstraint* | 约束尺寸指针。 |

### OH_ArkUI_NodeCustomEvent_GetPositionInLayout()

```
ArkUI_IntOffset OH_ArkUI_NodeCustomEvent_GetPositionInLayout(ArkUI_NodeCustomEvent* event)
```

**描述：**


通过自定义组件事件获取在布局阶段期望自身相对父组件的位置。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | 自定义组件事件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md) | 期望自身相对父组件的位置。 |

### OH_ArkUI_NodeCustomEvent_GetDrawContextInDraw()

```
ArkUI_DrawContext* OH_ArkUI_NodeCustomEvent_GetDrawContextInDraw(ArkUI_NodeCustomEvent* event)
```

**描述：**


通过自定义组件事件获取绘制上下文。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | 自定义组件事件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_DrawContext* | 绘制上下文。 |

### OH_ArkUI_NodeCustomEvent_GetEventTargetId()

```
int32_t OH_ArkUI_NodeCustomEvent_GetEventTargetId(ArkUI_NodeCustomEvent* event)
```

**描述：**


通过自定义组件事件获取自定义事件ID。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | 自定义组件事件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 自定义事件ID。 |

### OH_ArkUI_NodeCustomEvent_GetUserData()

```
void* OH_ArkUI_NodeCustomEvent_GetUserData(ArkUI_NodeCustomEvent* event)
```

**描述：**


通过自定义组件事件获取自定义事件参数。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | 自定义组件事件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| void* | 自定义事件参数。 |

### OH_ArkUI_NodeCustomEvent_GetNodeHandle()

```
ArkUI_NodeHandle OH_ArkUI_NodeCustomEvent_GetNodeHandle(ArkUI_NodeCustomEvent* event)
```

**描述：**


通过自定义组件事件获取组件对象。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | 自定义组件事件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | 组件对象。 |

### OH_ArkUI_NodeCustomEvent_GetEventType()

```
ArkUI_NodeCustomEventType OH_ArkUI_NodeCustomEvent_GetEventType(ArkUI_NodeCustomEvent* event)
```

**描述：**


通过自定义组件事件获取事件类型。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | 自定义组件事件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeCustomEventType](capi-native-node-h.md#arkui_nodecustomeventtype) | 组件自定义事件类型。 |

### OH_ArkUI_NodeCustomEvent_GetCustomSpanMeasureInfo()

```
int32_t OH_ArkUI_NodeCustomEvent_GetCustomSpanMeasureInfo(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanMeasureInfo* info)
```

**描述：**


通过自定义组件事件获取自定义段落组件的测量信息。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | 自定义组件事件。 |
| [ArkUI_CustomSpanMeasureInfo](capi-arkui-nativemodule-arkui-customspanmeasureinfo.md)* info | 需要获取的测量信息。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>        [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>        [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。<br>        异常原因：传入参数验证失败，参数不能为空。 |

### OH_ArkUI_NodeCustomEvent_SetCustomSpanMetrics()

```
int32_t OH_ArkUI_NodeCustomEvent_SetCustomSpanMetrics(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanMetrics* metrics)
```

**描述：**


通过自定义组件事件设置自定义段落的度量指标。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | 自定义组件事件。 |
| [ArkUI_CustomSpanMetrics](capi-arkui-nativemodule-arkui-customspanmetrics.md)* metrics | 需要获取的度量指标信息。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>        [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>        [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。<br>        异常原因：传入参数验证失败，参数不能为空。 |

### OH_ArkUI_NodeCustomEvent_GetCustomSpanDrawInfo()

```
int32_t OH_ArkUI_NodeCustomEvent_GetCustomSpanDrawInfo(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanDrawInfo* info)
```

**描述：**


通过自定义组件事件获取自定义段落组件的绘制信息。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | 自定义组件事件。 |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* info | 需要获取的绘制信息。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>        [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>        [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。<br>        异常原因：传入参数验证失败，参数不能为空。 |

### ArkUI_NodeContentCallback()

```
typedef void (*ArkUI_NodeContentCallback)(ArkUI_NodeContentEvent* event)
```

**描述：**


定义NodeContent事件的回调函数类型。

**起始版本：** 12

### OH_ArkUI_NodeContent_RegisterCallback()

```
int32_t OH_ArkUI_NodeContent_RegisterCallback(ArkUI_NodeContentHandle content, ArkUI_NodeContentCallback callback)
```

**描述：**


注册NodeContent事件函数。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontent8h.md) content | 需要注册事件的NodeContent对象。 |
| [ArkUI_NodeContentCallback](capi-native-node-h.md#arkui_nodecontentcallback) callback | 事件触发时需要执行的函数回调。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeContentEvent_GetEventType()

```
ArkUI_NodeContentEventType OH_ArkUI_NodeContentEvent_GetEventType(ArkUI_NodeContentEvent* event)
```

**描述：**


获取触发NodeContent事件的事件类型。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeContentEvent](capi-arkui-nativemodule-arkui-nodecontentevent.md)* event | NodeContent事件指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeContentEventType](capi-native-node-h.md#arkui_nodecontenteventtype) | NodeContent事件类型。 |

### OH_ArkUI_NodeContentEvent_GetNodeContentHandle()

```
ArkUI_NodeContentHandle OH_ArkUI_NodeContentEvent_GetNodeContentHandle(ArkUI_NodeContentEvent* event)
```

**描述：**


获取触发事件的NodeContent对象。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeContentEvent](capi-arkui-nativemodule-arkui-nodecontentevent.md)* event | NodeContent事件指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontent8h.md) | Returns 触发事件的NodeContent对象。 |

### OH_ArkUI_NodeContent_SetUserData()

```
int32_t OH_ArkUI_NodeContent_SetUserData(ArkUI_NodeContentHandle content, void* userData)
```

**描述：**


在NodeContent对象上保存自定义数据。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontent8h.md) content | 需要保存自定义数据的NodeContent对象。 |
| void* userData | 要保存的自定义数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeContent_GetUserData()

```
void* OH_ArkUI_NodeContent_GetUserData(ArkUI_NodeContentHandle content)
```

**描述：**


获取在NodeContent对象上保存的自定义数据。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontent8h.md) content | 需要保存自定义数据的NodeContent对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| void* | 自定义数据。 |

### OH_ArkUI_NodeContent_AddNode()

```
int32_t OH_ArkUI_NodeContent_AddNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node)
```

**描述：**


将一个ArkUI组件节点添加到对应的NodeContent对象下。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontent8h.md) content | 需要被添加节点的NodeContent对象。 |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 需要被添加的节点。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeContent_RemoveNode()

```
int32_t OH_ArkUI_NodeContent_RemoveNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node)
```

**描述：**


删除NodeContent对象下的一个ArkUI组件节点。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontent8h.md) content | 需要被删除节点的NodeContent对象。 |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 需要被删除的节点。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeContent_InsertNode()

```
int32_t OH_ArkUI_NodeContent_InsertNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node, int32_t position)
```

**描述：**


将一个ArkUI组件节点插入到对应的NodeContent对象的特定位置下。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontent8h.md) content | 需要被插入节点的NodeContent对象。 |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 需要被插入的节点。 |
| int32_t position | 需要被插入的位置。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetLayoutSize()

```
int32_t OH_ArkUI_NodeUtils_GetLayoutSize(ArkUI_NodeHandle node, ArkUI_IntSize* size)
```

**描述：**


获取组件布局区域的大小。布局区域大小不包含图形变化属性，如缩放。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle指针。 |
| [ArkUI_IntSize](capi-arkui-nativemodule-arkui-intsize.md)* size | 组件handle的绘制区域尺寸，单位：px。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetLayoutPosition()

```
int32_t OH_ArkUI_NodeUtils_GetLayoutPosition(ArkUI_NodeHandle node, ArkUI_IntOffset* localOffset)
```

**描述：**


获取组件布局区域相对父组件的位置。布局区域相对位置不包含图形变化属性，如平移。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle指针。 |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* localOffset | 组件handle相对父组件的偏移值，单位：px。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetLayoutPositionInWindow()

```
int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInWindow(ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset)
```

**描述：**


获取组件布局区域相对窗口的位置。布局区域相对位置不包含图形变化属性，如平移。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle指针。 |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* globalOffset | 组件handle相对窗口的偏移值，单位：px。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetLayoutPositionInScreen()

```
int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInScreen(ArkUI_NodeHandle node, ArkUI_IntOffset* screenOffset)
```

**描述：**


获取组件布局区域相对屏幕的位置。布局区域相对位置不包含图形变化属性，如平移。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle指针。 |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* screenOffset | 组件handle相对屏幕的偏移值，单位：px。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetLayoutPositionInGlobalDisplay()

```
int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInGlobalDisplay(ArkUI_NodeHandle node, ArkUI_IntOffset* offset)
```

**描述：**


获取组件相对于全局屏幕的偏移。布局区域相对位置不包含图形变化属性，如平移。

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle指针。 |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* offset | 组件handle相对屏幕的偏移值，单位：px。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetPositionWithTranslateInWindow()

```
int32_t OH_ArkUI_NodeUtils_GetPositionWithTranslateInWindow(ArkUI_NodeHandle node, ArkUI_IntOffset* translateOffset)
```

**描述：**


获取组件在窗口中的位置，包含了图形平移变化属性。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle指针。 |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* translateOffset | 组件handle自身，父组件及祖先节点的偏移累计值，单位：px。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetPositionWithTranslateInScreen()

```
int32_t OH_ArkUI_NodeUtils_GetPositionWithTranslateInScreen(ArkUI_NodeHandle node, ArkUI_IntOffset* translateOffset)
```

**描述：**


获取组件在屏幕中的位置，包含了图形平移变化属性。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle指针。 |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* translateOffset | 组件handle自身，父组件及祖先节点的偏移累计值，单位：px。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_AddCustomProperty()

```
void OH_ArkUI_NodeUtils_AddCustomProperty(ArkUI_NodeHandle node, const char* name, const char* value)
```

**描述：**


设置组件的自定义属性。该接口仅在主线程生效。

**起始版本：** 13


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle指针。 |
| const char* name | 自定义属性的名称。不允许传入空指针。 |
| const char* value | 对应key参数名称的自定义属性的值。不允许传入空指针。 |

### OH_ArkUI_NodeUtils_RemoveCustomProperty()

```
void OH_ArkUI_NodeUtils_RemoveCustomProperty(ArkUI_NodeHandle node, const char* name)
```

**描述：**


移除组件已设置的自定义属性。

**起始版本：** 13


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle指针。 |
| const char* name | 自定义属性的名称。 |

### OH_ArkUI_NodeUtils_GetCustomProperty()

```
int32_t OH_ArkUI_NodeUtils_GetCustomProperty(ArkUI_NodeHandle node, const char* name, ArkUI_CustomProperty** handle)
```

**描述：**


获取组件的自定义属性的值。

**起始版本：** 14


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle指针。 |
| const char* name | 自定义属性的名称。 |
| [ArkUI_CustomProperty](capi-arkui-nativemodule-arkui-customproperty.md)** handle | 获取的对应key参数名称的自定义属性的结构体。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetParentInPageTree()

```
ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetParentInPageTree(ArkUI_NodeHandle node)
```

**描述：**


获取父节点，可获取由ArkTs创建的组件节点。

**起始版本：** 14


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | 组件的指针，如果没有返回NULL。 |

### OH_ArkUI_NodeUtils_GetActiveChildrenInfo()

```
int32_t OH_ArkUI_NodeUtils_GetActiveChildrenInfo(ArkUI_NodeHandle head, ArkUI_ActiveChildrenInfo** handle)
```

**描述：**


获取某个节点所有活跃的子节点。Span将不会被计入子结点的统计中。

**起始版本：** 14


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) head | 传入需要获取的节点。 |
| [ArkUI_ActiveChildrenInfo](capi-arkui-nativemodule-arkui-activechildreninfo.md)** handle | 对应head节点子节点信息的结构体。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetCurrentPageRootNode()

```
ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetCurrentPageRootNode(ArkUI_NodeHandle node)
```

**描述：**


获取当前页面的根节点。

**起始版本：** 14


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | 根节点的指针，如果没有返回NULL。 |

### OH_ArkUI_NodeUtils_IsCreatedByNDK()

```
bool OH_ArkUI_NodeUtils_IsCreatedByNDK(ArkUI_NodeHandle node)
```

**描述：**


获取组件是否由C-API创建的标签。

**起始版本：** 14


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 节点是否由C-API创建的Tag，true代表由C-API创建，false代表非C-API创建。 |

### OH_ArkUI_NodeUtils_GetNodeType()

```
int32_t OH_ArkUI_NodeUtils_GetNodeType(ArkUI_NodeHandle node)
```

**描述：**


获取节点的类型。

**起始版本：** 14


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 节点的类型，具体已开放类型参考[ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype)，未开放结点返回-1。 |

### OH_ArkUI_NodeUtils_GetWindowInfo()

```
int32_t OH_ArkUI_NodeUtils_GetWindowInfo(ArkUI_NodeHandle node, ArkUI_HostWindowInfo** info)
```

**描述：**


获取节点所属的窗口信息。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点对象。 |
| [ArkUI_HostWindowInfo](capi-arkui-nativemodule-arkui-hostwindowinfo.md)** info | 窗口信息。使用[OH_ArkUI_HostWindowInfo_Destroy](capi-native-type-h.md#oh_arkui_hostwindowinfo_destroy)释放内存。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。<br>         [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) CAPI初始化错误。<br>         [ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE](capi-native-type-h.md#arkui_errorcode) 节点未挂载到节点树上。 |

### OH_ArkUI_NodeUtils_MoveTo()

```
int32_t OH_ArkUI_NodeUtils_MoveTo(ArkUI_NodeHandle node, ArkUI_NodeHandle target_parent, int32_t index)
```

**描述：**


将节点移动到目标父节点下，作为子节点。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 待移动的节点对象。 |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) target_parent | 目标父节点指针。 |
| int32_t index | 转移后的节点下标，如果下标值为非法值，则添加在目标父节点的最后一位。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。<br>         [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) CAPI初始化错误。 |

### OH_ArkUI_List_CloseAllSwipeActions()

```
int32_t OH_ArkUI_List_CloseAllSwipeActions(ArkUI_NodeHandle node, void* userData, void (*onFinish)(void* userData))
```

**描述：**


收起展开状态下的ListItem。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| node | 需要注册事件的节点对象。 |
| void* userData | 自定义事件参数，当事件触发时在回调参数中携带回来。 |
| onFinish | 在收起动画完成后触发的回调。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t (ArkUI_NodeHandle node, void* userData, void (*onFinish) | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。<br>         [ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED](capi-native-type-h.md#arkui_errorcode) 组件不支持该事件。 |

### OH_ArkUI_GetContextByNode()

```
ArkUI_ContextHandle OH_ArkUI_GetContextByNode(ArkUI_NodeHandle node)
```

**描述：**


获取当前节点所在页面的UI的上下文实例对象指针。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 指定的节点。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) | UI的上下文实例对象指针。 |

### OH_ArkUI_RegisterSystemColorModeChangeEvent()

```
int32_t OH_ArkUI_RegisterSystemColorModeChangeEvent(ArkUI_NodeHandle node,void* userData, void (*onColorModeChange)(ArkUI_SystemColorMode colorMode, void* userData))
```

**描述：**


注册系统深浅色变更事件。同一组件仅能注册一个系统深浅变更回调。示例请参考：[监听组件事件](../../ui/ndk-listen-to-component-events.md)。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| node | 指定的节点。 |
|  void* userData | 自定义事件参数，当事件触发时在回调参数中携带回来。 |
| onColorModeChange | 事件触发后的回调。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t  | 错误码。<br>        [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>        [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。<br>        [ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED](capi-native-type-h.md#arkui_errorcode) 组件不支持该事件。 |

### OH_ArkUI_UnregisterSystemColorModeChangeEvent()

```
void OH_ArkUI_UnregisterSystemColorModeChangeEvent(ArkUI_NodeHandle node)
```

**描述：**


注销系统深浅色变更事件。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 指定的节点。 |

### OH_ArkUI_RegisterSystemFontStyleChangeEvent()

```
int32_t OH_ArkUI_RegisterSystemFontStyleChangeEvent(ArkUI_NodeHandle node,void* userData, void (*onFontStyleChange)(ArkUI_SystemFontStyleEvent* event, void* userData))
```

**描述：**


注册系统字体变更事件。同一组件仅能注册一个系统字体变更回调。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| node | 指定的节点。 |
|  void* userData | 自定义事件参数，当事件触发时在回调参数中携带回来。 |
| onFontStyleChange | 事件触发后的回调。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t  | 错误码。<br>        [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>        [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。<br>        [ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED](capi-native-type-h.md#arkui_errorcode) 组件不支持该事件。 |

### OH_ArkUI_UnregisterSystemFontStyleChangeEvent()

```
void OH_ArkUI_UnregisterSystemFontStyleChangeEvent(ArkUI_NodeHandle node)
```

**描述：**


注销系统字体变更事件。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 指定的节点。 |

### OH_ArkUI_SystemFontStyleEvent_GetFontSizeScale()

```
float OH_ArkUI_SystemFontStyleEvent_GetFontSizeScale(const ArkUI_SystemFontStyleEvent* event)
```

**描述：**


获取系统字体变更事件的字体大小值。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_SystemFontStyleEvent](capi-arkui-nativemodule-arkui-systemfontstyleevent.md)* event | 表示指向当前系统字体变更事件的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 更新后的系统字体大小缩放系数。默认值：1.0。 |

### OH_ArkUI_SystemFontStyleEvent_GetFontWeightScale()

```
float OH_ArkUI_SystemFontStyleEvent_GetFontWeightScale(const ArkUI_SystemFontStyleEvent* event)
```

**描述：**


获取系统字体变更事件的字体粗细值。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_SystemFontStyleEvent](capi-arkui-nativemodule-arkui-systemfontstyleevent.md)* event | 表示指向当前系统字体变更事件的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 更新后的系统字体粗细缩放系数。默认值：1.0。 |

### OH_ArkUI_RegisterLayoutCallbackOnNodeHandle()

```
int32_t OH_ArkUI_RegisterLayoutCallbackOnNodeHandle(ArkUI_NodeHandle node,void* userData, void (*onLayoutCompleted)(void* userData))
```

**描述：**


注册指定节点的布局完成回调函数。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| node | 指定需要注册回调函数的目标节点。 |
| void* userData | 执行回调函数时传给回调函数的用户自定义参数。 |
| onLayoutCompleted | 布局完成时的回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t  | 错误码。<br>          [ARKUI_INSPECTOR_NATIVE_RESULT_SUCCESSFUL](capi-native-node-h.md#arkui_inspectorerrorcode) 成功。<br>         [ARKUI_INSPECTOR_NATIVE_RESULT_BAD_PARAMETER](capi-native-node-h.md#arkui_inspectorerrorcode) 参数错误。 |

### OH_ArkUI_RegisterDrawCallbackOnNodeHandle()

```
int32_t OH_ArkUI_RegisterDrawCallbackOnNodeHandle(ArkUI_NodeHandle node,void* userData, void (*onDrawCompleted)(void* userData))
```

**描述：**


注册指定节点的绘制完成回调函数。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| node | 指定需要注册回调函数的目标节点。 |
| void* userData | 执行回调函数时传给回调函数的用户自定义参数。 |
| onDrawCompleted | 绘制完成时的回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t  | 错误码。<br>          [ARKUI_INSPECTOR_NATIVE_RESULT_SUCCESSFUL](capi-native-node-h.md#arkui_inspectorerrorcode) 成功。<br>         [ARKUI_INSPECTOR_NATIVE_RESULT_BAD_PARAMETER](capi-native-node-h.md#arkui_inspectorerrorcode) 参数错误。 |

### OH_ArkUI_UnregisterLayoutCallbackOnNodeHandle()

```
int32_t OH_ArkUI_UnregisterLayoutCallbackOnNodeHandle(ArkUI_NodeHandle node)
```

**描述：**


取消注册指定节点的布局完成回调函数。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 指定需要取消注册回调函数的目标节点。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>          [ARKUI_INSPECTOR_NATIVE_RESULT_SUCCESSFUL](capi-native-node-h.md#arkui_inspectorerrorcode) 成功。<br>         [ARKUI_INSPECTOR_NATIVE_RESULT_BAD_PARAMETER](capi-native-node-h.md#arkui_inspectorerrorcode) 参数错误。 |

### OH_ArkUI_UnregisterDrawCallbackOnNodeHandle()

```
int32_t OH_ArkUI_UnregisterDrawCallbackOnNodeHandle(ArkUI_NodeHandle node)
```

**描述：**


取消注册指定节点的绘制完成回调函数。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 指定需要取消注册回调函数的目标节点。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>          [ARKUI_INSPECTOR_NATIVE_RESULT_SUCCESSFUL](capi-native-node-h.md#arkui_inspectorerrorcode) 成功。<br>         [ARKUI_INSPECTOR_NATIVE_RESULT_BAD_PARAMETER](capi-native-node-h.md#arkui_inspectorerrorcode) 参数错误。 |

### OH_ArkUI_GetNodeSnapshot()

```
int32_t OH_ArkUI_GetNodeSnapshot(ArkUI_NodeHandle node, ArkUI_SnapshotOptions* snapshotOptions,OH_PixelmapNative** pixelmap)
```

**描述：**


获取给定组件的截图，若节点不在组件树上或尚未渲染，截图操作将会失败。当pixelmap不再使用时，应通过调用OH_PixelmapNative_Release来释放。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 截图的目标节点。 |
| [ArkUI_SnapshotOptions](capi-arkui-nativemodule-arkui-snapshotoptions.md)* snapshotOptions | 给定的截图配置，为空时表示默认配置。 |
| OH_PixelmapNative** pixelmap | 通过系统创建的Pixelmap指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。<br>         [ARKUI_ERROR_CODE_INTERNAL_ERROR](capi-native-type-h.md#arkui_errorcode) 截图失败，将返回空指针。<br>         [ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_TIMEOUT](capi-native-type-h.md#arkui_errorcode) 截图超时。 |

### OH_ArkUI_NodeUtils_GetAttachedNodeHandleById()

```
int32_t OH_ArkUI_NodeUtils_GetAttachedNodeHandleById(const char* id, ArkUI_NodeHandle* node)
```

**描述：**


根据用户id获取目标节点。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* id | 目标节点的id。 |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)* node | 目标节点的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetNodeHandleByUniqueId()

```
int32_t OH_ArkUI_NodeUtils_GetNodeHandleByUniqueId(const uint32_t uniqueId, ArkUI_NodeHandle* node)
```

**描述：**


通过uniqueId获取节点。

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const uint32_t uniqueId | 目标节点的uniqueId。 |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)* node | 目标节点的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 方法参数错误。<br>         [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) CAPI初始化错误。 |

### OH_ArkUI_NodeUtils_GetNodeUniqueId()

```
int32_t OH_ArkUI_NodeUtils_GetNodeUniqueId(ArkUI_NodeHandle node, int32_t* uniqueId)
```

**描述：**


获取目标节点的uniqueId。

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI节点指针。 |
| int32_t* uniqueId | 目标节点的uniqueId。组件标识ID只读，且进程内唯一，若该节点存在，返回该节点的uniqueld值；否则返回-1。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 方法参数错误。<br>         [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) CAPI初始化错误。 |

### OH_ArkUI_NodeUtils_SetCrossLanguageOption()

```
int32_t OH_ArkUI_NodeUtils_SetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)
```

**描述：**


设置目标节点跨语言设置属性的能力。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点的指针。 |
| [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)* option | 跨语言配置项 [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetCrossLanguageOption()

```
int32_t OH_ArkUI_NodeUtils_GetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)
```

**描述：**


获取目标节点跨语言设置属性的配置项。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点的指针。 |
| [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)* option | 跨语言配置项 [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetFirstChildIndexWithoutExpand()

```
int32_t OH_ArkUI_NodeUtils_GetFirstChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)
```

**描述：**


获取目标节点在树上的第一个子节点的下标。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点的指针。 |
| uint32_t* index | 子节点的下标值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetLastChildIndexWithoutExpand()

```
int32_t OH_ArkUI_NodeUtils_GetLastChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)
```

**描述：**


获取目标节点在树上的最后一个子节点的下标。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点的指针。 |
| uint32_t* index | 子节点的下标值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetChildWithExpandMode()

```
int32_t OH_ArkUI_NodeUtils_GetChildWithExpandMode(ArkUI_NodeHandle node, int32_t position,ArkUI_NodeHandle* subnode, uint32_t expandMode)
```

**描述：**


用不同的展开模式获取对应下标的子节点。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点的指针。 |
| int32_t position | 对应子节点的下标。 |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)* subnode | 获取子节点的指针。 |
| uint32_t expandMode | 节点遍历展开方式。 [ArkUI_ExpandMode](capi-native-type-h.md#arkui_expandmode)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetPositionToParent()

```
int32_t OH_ArkUI_NodeUtils_GetPositionToParent(ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset)
```

**描述：**


获取目标节点相对于父节点的偏移值，单位：px。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点。 |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* globalOffset | 目标节点相对父节点的偏移值，单位：px。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_AddSupportedUIStates()

```
ArkUI_ErrorCode OH_ArkUI_AddSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates,void (statesChangeHandler)(int32_t currentStates, void* userData), bool excludeInner, void* userData)
```

**描述：**


设置组件支持的多态样式状态。为了更高效地处理，需传入所关注的状态值及对应的状态处理函数，当关注的状态发生时，处理函数会被执行。可在回调中根据当前状态调整UI样式。当在同一个节点上多次调用该方法时，将以最后一次传入的状态及处理函数为准。有些类型的组件节点，系统内部已有对某些状态的默认处理。例如，Button组件默认具备对PRESSED状态的样式变化，当在此类组件上使用此方法自定义状态处理时，会先应用系统默认样式变化，再执行自定义的样式处理，最终效果为两者叠加。可以通过指定excludeInner为true来禁用系统内部的默认样式效果，但这通常取决于系统内部实现规范是否允许。当调用该函数时，传入的statesChangeHandler函数会立即执行一次，且无需特意注册对NORMAL状态的监听，只要注册了非NORMAL状态，当状态从任意状态变化回NORMAL时，系统都会进行回调，以便应用进行样式复原。

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| node | 目标节点。 |
| uiStates | 目标节点需要处理的目标UI状态。所有目标UI状态的组合结果可以通过“|”操作来计算。例如：targetUIStates = ArkUI_UIState::PRESSED | ArkUI_UIState::FOCUSED。 |
| statesChangeHandler | UI状态改变处理函数。返回当前UI状态，该值是所有当前状态枚举值“|”计算的结果，可以通过执行“&”操作来确定状态。例如：if (currentStates & ArkUI_UIState::PRESSED == ArkUI_UIState::PRESSED)。但是，对于正常状态检查，应直接使用等号。例如：if (currentStates == ArkUI_UIState::NORMAL) |
|  bool excludeInner | 禁止内部默认状态样式的标志。 |
|  void* userData | onDrawCompleted回调函数中使用的自定义数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode (ArkUI_NodeHandle node, int32_t uiStates,void (statesChangeHandler) | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_RemoveSupportedUIStates()

```
ArkUI_ErrorCode OH_ArkUI_RemoveSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates)
```

**描述：**


删除注册的状态处理。当通过OH_ArkUI_AddSupportedUIStates注册的状态都被删除时，所注册的stateChangeHandler也不会再被执行。

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点。 |
| int32_t uiStates | 节点需要删除的目标UI状态。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_RunTaskInScope()

```
int32_t OH_ArkUI_RunTaskInScope(ArkUI_ContextHandle uiContext, void* userData, void(*callback)(void* userData))
```

**描述：**


在目标UI上下文中执行传入的自定义回调函数。示例请参考：[在NDK中保证多实例场景功能正常](../../ui/ndk-scope-task.md)。

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| uiContext | 表示目标UI上下文的指针。 |
| void* userData | 开发者自定义数据指针，以便在回调函数中处理自定义数据，开发者需自行保证自定义函数被执行时的数据有效性。 |
| callback | 开发者自定义回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t (ArkUI_ContextHandle uiContext, void* userData, void(*callback) | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) CAPI初始化错误。<br>         [ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](capi-native-type-h.md#arkui_errorcode) UIContext对象无效。<br>         [ARKUI_ERROR_CODE_CALLBACK_INVALID](capi-native-type-h.md#arkui_errorcode) 回调函数无效。 |


