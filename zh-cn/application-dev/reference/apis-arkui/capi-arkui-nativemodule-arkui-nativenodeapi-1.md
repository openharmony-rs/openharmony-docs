# ArkUI_NativeNodeAPI_1
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @piggyguy; @wangyang2022-->
<!--Designer: @piggyguy; @wangyang2022-->
<!--Tester: @fredyuan912-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ArkUI_NativeNodeAPI_1
```

## 概述

ArkUI提供的Native侧Node类型接口集合，支持组件节点的创建与销毁、节点树操作、属性与事件管理、测量和布局等能力，适用于使用Native API构建和操作ArkUI组件节点的场景。Node模块相关接口需要在主线程上调用。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t version | 结构体版本，当前使用的ArkUI_NativeNodeAPI_1结构体的版本编号，由系统提供，开发者无需修改。 |


### 成员函数

| 名称 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle (\*createNode)(ArkUI_NodeType type)](#createnode) | 基于[ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype)生成对应的组件并返回组件对象指针。 |
| [void (\*disposeNode)(ArkUI_NodeHandle node)](#disposenode) | 销毁组件指针指向的组件对象。 |
| [int32_t (\*addChild)(ArkUI_NodeHandle parent, ArkUI_NodeHandle child)](#addchild) | 将组件挂载到某个父节点之下。 |
| [int32_t (\*removeChild)(ArkUI_NodeHandle parent, ArkUI_NodeHandle child)](#removechild) | 将组件从父节点中移除。 |
| [int32_t (\*insertChildAfter)(ArkUI_NodeHandle parent, ArkUI_NodeHandle child, ArkUI_NodeHandle sibling)](#insertchildafter) | 将组件挂载到某个父节点之下，挂载位置在<b>sibling</b>节点之后。 |
| [int32_t (\*insertChildBefore)(ArkUI_NodeHandle parent, ArkUI_NodeHandle child, ArkUI_NodeHandle sibling)](#insertchildbefore) | 将组件挂载到某个父节点之下，挂载位置在<b>sibling</b>节点之前。 |
| [int32_t (\*insertChildAt)(ArkUI_NodeHandle parent, ArkUI_NodeHandle child, int32_t position)](#insertchildat) | 将组件挂载到某个父节点之下，挂载位置由<b>position</b>指定。 |
| [int32_t (\*setAttribute)(ArkUI_NodeHandle node, ArkUI_NodeAttributeType attribute, const ArkUI_AttributeItem* item)](#setattribute) | 属性设置函数。 |
| [const ArkUI_AttributeItem* (\*getAttribute)(ArkUI_NodeHandle node, ArkUI_NodeAttributeType attribute)](#getattribute) | 属性获取函数。该接口返回的指针是ArkUI框架内部的缓冲区指针，不需要开发者主动调用delete释放内存，但是需要在该函数下一次被调用前使用，否则可能会被其他值所覆盖。 |
| [int32_t (\*resetAttribute)(ArkUI_NodeHandle node, ArkUI_NodeAttributeType attribute)](#resetattribute) | 重置属性函数。 |
| [int32_t (\*registerNodeEvent)(ArkUI_NodeHandle node, ArkUI_NodeEventType eventType, int32_t targetId, void* userData)](#registernodeevent) | 注册节点事件函数。事件触发后，可通过[addNodeEventReceiver](#addnodeeventreceiver)添加的组件级回调或[registerNodeEventReceiver](#registernodeeventreceiver)注册的全局回调接收；不再需要该事件时，可调用[unregisterNodeEvent](#unregisternodeevent)反注册。 |
| [void (\*unregisterNodeEvent)(ArkUI_NodeHandle node, ArkUI_NodeEventType eventType)](#unregisternodeevent) | 反注册此前通过[registerNodeEvent](#registernodeevent)注册的节点事件。反注册后，该事件不再触发相应回调。 |
| [void (\*registerNodeEventReceiver)(void (\*eventReceiver)(ArkUI_NodeEvent* event))](#registernodeeventreceiver) | 注册事件回调统一入口函数。ArkUI框架会统一收集过程中产生的组件事件并通过注册的eventReceiver函数回调给开发者。<br> 重复调用时会覆盖前一次注册的函数。<br> 避免直接保存[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象指针，数据会在回调结束后销毁。<br> 如果需要和组件实例绑定，可以使用[addNodeEventReceiver](#addnodeeventreceiver)函数接口。<br> 不再需要全局回调时，可调用[unregisterNodeEventReceiver](#unregisternodeeventreceiver)反注册。<br> |
| [void (\*unregisterNodeEventReceiver)()](#unregisternodeeventreceiver) | 反注册通过[registerNodeEventReceiver](#registernodeeventreceiver)注册的全局事件回调统一入口函数。反注册后，全局入口不再接收组件事件。 |
| [void (\*markDirty)(ArkUI_NodeHandle node, ArkUI_NodeDirtyFlag dirtyFlag)](#markdirty) | 强制标记当前节点需要重新测量、布局或绘制。系统属性更新时，ArkUI框架会自动标记节点并重新执行相应流程，无需开发者主动调用该函数；当开发者修改框架无法自动感知的自定义测量、布局或绘制数据时，可调用该函数触发对应流程。 |
| [uint32_t (\*getTotalChildCount)(ArkUI_NodeHandle node)](#gettotalchildcount) | 获取子节点的个数。 |
| [ArkUI_NodeHandle (\*getChildAt)(ArkUI_NodeHandle node, int32_t position)](#getchildat) | 获取指定索引位置的子节点。 |
| [ArkUI_NodeHandle (\*getFirstChild)(ArkUI_NodeHandle node)](#getfirstchild) | 获取第一个子节点。 |
| [ArkUI_NodeHandle (\*getLastChild)(ArkUI_NodeHandle node)](#getlastchild) | 获取最后一个子节点。 |
| [ArkUI_NodeHandle (\*getPreviousSibling)(ArkUI_NodeHandle node)](#getprevioussibling) | 获取上一个兄弟节点。 |
| [ArkUI_NodeHandle (\*getNextSibling)(ArkUI_NodeHandle node)](#getnextsibling) | 获取下一个兄弟节点。 |
| [int32_t (\*registerNodeCustomEvent)(ArkUI_NodeHandle node, ArkUI_NodeCustomEventType eventType, int32_t targetId, void* userData)](#registernodecustomevent) | 注册自定义节点事件函数。事件触发后，可通过[addNodeCustomEventReceiver](#addnodecustomeventreceiver)添加的组件级回调或[registerNodeCustomEventReceiver](#registernodecustomeventreceiver)注册的全局回调接收；不再需要该事件时，可调用[unregisterNodeCustomEvent](#unregisternodecustomevent)反注册。 |
| [void (\*unregisterNodeCustomEvent)(ArkUI_NodeHandle node, ArkUI_NodeCustomEventType eventType)](#unregisternodecustomevent) | 反注册此前通过[registerNodeCustomEvent](#registernodecustomevent)注册的自定义节点事件。反注册后，该事件不再触发相应回调。 |
| [void (\*registerNodeCustomEventReceiver)(void (\*eventReceiver)(ArkUI_NodeCustomEvent* event))](#registernodecustomeventreceiver) | 注册自定义节点事件回调统一入口函数。ArkUI框架会统一收集过程中产生的自定义组件事件并通过注册的registerNodeCustomEventReceiver函数回调给开发者。<br> 重复调用时会覆盖前一次注册的函数。<br> 避免直接保存[ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)对象指针，数据会在回调结束后销毁。<br> 如果需要和组件实例绑定，可以使用[addNodeCustomEventReceiver](#addnodecustomeventreceiver)函数接口。<br> 不再需要全局回调时，可调用[unregisterNodeCustomEventReceiver](#unregisternodecustomeventreceiver)反注册。<br> |
| [void (\*unregisterNodeCustomEventReceiver)()](#unregisternodecustomeventreceiver) | 反注册通过[registerNodeCustomEventReceiver](#registernodecustomeventreceiver)注册的全局自定义事件回调统一入口函数。反注册后，全局入口不再接收自定义组件事件。 |
| [int32_t (\*setMeasuredSize)(ArkUI_NodeHandle node, int32_t width, int32_t height)](#setmeasuredsize) | 在测算回调函数中设置组件测算完成后的宽度和高度。 |
| [int32_t (\*setLayoutPosition)(ArkUI_NodeHandle node, int32_t positionX, int32_t positionY)](#setlayoutposition) | 在布局回调函数中设置组件相对于父组件的布局位置。该接口优先级低于ArkUI_NodeAttributeType中的[NODE_POSITION](capi-native-node-h-nodeattributetype-layoutattributes.md#node_position)。 |
| [ArkUI_IntSize (\*getMeasuredSize)(ArkUI_NodeHandle node)](#getmeasuredsize) | 获取组件测算完成后的宽高尺寸。 |
| [ArkUI_IntOffset (\*getLayoutPosition)(ArkUI_NodeHandle node)](#getlayoutposition) | 获取组件布局完成后该节点相对于父节点的偏移，单位为px。该偏移是父容器对该节点进行布局之后的结果，因此布局之后生效的offset属性和不参与布局的position属性不影响该偏移值。 |
| [int32_t (\*measureNode)(ArkUI_NodeHandle node, ArkUI_LayoutConstraint* Constraint)](#measurenode) | 对目标组件进行测算，可以通过getMeasuredSize接口获取测算后的大小。 |
| [int32_t (\*layoutNode)(ArkUI_NodeHandle node, int32_t positionX, int32_t positionY)](#layoutnode) | 对目标组件进行布局并传递该组件相对父组件的期望位置。 |
| [int32_t (\*addNodeEventReceiver)(ArkUI_NodeHandle node, void (\*eventReceiver)(ArkUI_NodeEvent* event))](#addnodeeventreceiver) | 在组件上添加组件事件回调函数，用于接收该组件产生的组件事件。不同于registerNodeEventReceiver的全局注册函数，该函数允许在同一个组件上添加多个事件接收器。<br> 该函数添加的监听回调函数触发时机会先于registerNodeEventReceiver注册的全局回调函数。<br> 避免直接保存[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象指针，数据会在回调结束后销毁。<br> 不再需要该回调时，可调用[removeNodeEventReceiver](#removenodeeventreceiver)删除。<br> |
| [int32_t (\*removeNodeEventReceiver)(ArkUI_NodeHandle node, void (\*eventReceiver)(ArkUI_NodeEvent* event))](#removenodeeventreceiver) | 删除此前通过[addNodeEventReceiver](#addnodeeventreceiver)添加到该组件的事件回调函数。删除后，该回调不再接收该组件产生的事件。 |
| [int32_t (\*addNodeCustomEventReceiver)(ArkUI_NodeHandle node, void (\*eventReceiver)(ArkUI_NodeCustomEvent* event))](#addnodecustomeventreceiver) | 在组件上添加自定义事件回调函数，用于接收该组件产生的自定义事件（如布局事件、绘制事件）。不同于registerNodeCustomEventReceiver的全局注册函数，该函数允许在同一个组件上添加多个事件接收器。<br> 该函数添加的监听回调函数触发时机会先于registerNodeCustomEventReceiver注册的全局回调函数。<br> 避免直接保存[ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)对象指针，数据会在回调结束后销毁。<br> 不再需要该回调时，可调用[removeNodeCustomEventReceiver](#removenodecustomeventreceiver)删除。<br> |
| [int32_t (\*removeNodeCustomEventReceiver)(ArkUI_NodeHandle node, void (\*eventReceiver)(ArkUI_NodeCustomEvent* event))](#removenodecustomeventreceiver) | 删除此前通过[addNodeCustomEventReceiver](#addnodecustomeventreceiver)添加到该组件的自定义事件回调函数。删除后，该回调不再接收该组件产生的自定义事件。 |
| [int32_t (\*setUserData)(ArkUI_NodeHandle node, void* userData)](#setuserdata) | 在组件上保存自定义数据。 |
| [void* (\*getUserData)(ArkUI_NodeHandle node)](#getuserdata) | 获取在组件上保存的自定义数据。 |
| [int32_t (\*setLengthMetricUnit)(ArkUI_NodeHandle node, ArkUI_LengthMetricUnit unit)](#setlengthmetricunit) | 指定组件通过Native Node API设置长度类属性时使用的单位。当业务需要统一使用px、vp或fp设置组件长度类属性时，可调用本接口指定单位。 |
| [ArkUI_NodeHandle (\*getParent)(ArkUI_NodeHandle node)](#getparent) | 获取父节点。 |
| [int32_t (\*removeAllChildren)(ArkUI_NodeHandle parent)](#removeallchildren) | 从父组件上卸载所有子节点。 |

## 成员函数说明

### createNode()

```c
ArkUI_NodeHandle (*createNode)(ArkUI_NodeType type)
```

**描述：**


基于[ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype)生成对应的组件并返回组件对象指针。

**起始版本：** 12

**参数：**

| 参数项                                                         | 描述 |
|-------------------------------------------------------------| -- |
| [ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype) type | 创建指定类型的UI组件节点。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | 返回创建完成的组件对象指针，如果创建失败返回NULL。组件对象不再使用时，应调用[disposeNode](#disposenode)销毁；未正确管理生命周期可能导致Use After Free、进程崩溃或内存泄漏。 |

### disposeNode()

```c
void (*disposeNode)(ArkUI_NodeHandle node)
```

**描述：**

销毁组件指针指向的组件对象。在非主线程调用时需要注意待销毁组件对象的生命周期，生命周期管理不当有可能导致应用崩溃，因此不建议在非主线程上调用本接口。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 组件指针对象。 |

### addChild()

```c
int32_t (*addChild)(ArkUI_NodeHandle parent, ArkUI_NodeHandle child)
```

**描述：**


将组件挂载到某个父节点之下。本接口属于节点操作接口，不建议在非主线程上调用。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) parent | 父节点指针。 |
|  [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) child | 子节点指针。 |

**返回：**

| 类型 | 说明                                                                                                                                                                                                                                                                                                                                     |
| -- |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| int32_t | 错误码。<br>             [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>             [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 函数参数异常。<br>             [ARKUI_ERROR_CODE_ARKTS_NODE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 不支持对ArkTS创建的节点执行对应的操作。 <br>             [ARKUI_ERROR_CODE_NODE_IS_ADOPTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 节点已被接纳为附属节点。从API version 22开始支持。|

### removeChild()

```c
int32_t (*removeChild)(ArkUI_NodeHandle parent, ArkUI_NodeHandle child)
```

**描述：**


将组件从父节点中移除。本接口属于节点操作接口，不建议在非主线程上调用。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) parent | 父节点指针。 |
|  [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) child | 子节点指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>             [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>             [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 函数参数异常。<br>             [ARKUI_ERROR_CODE_ARKTS_NODE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 不支持对ArkTS创建的节点执行对应的操作。<br>             [ARKUI_ERROR_CODE_ADAPTER_EXIST](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) NodeAdapter已经存在。|

### insertChildAfter()

```c
int32_t (*insertChildAfter)(ArkUI_NodeHandle parent, ArkUI_NodeHandle child, ArkUI_NodeHandle sibling)
```

**描述：**


将组件挂载到某个父节点之下，挂载位置在<b>sibling</b>节点之后。本接口属于节点操作接口，不建议在非主线程上调用。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) parent | 父节点指针。 |
|  [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) child | 子节点指针。 |
|  [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) sibling | 前一个兄弟节点指针，如果为空则插入位置在最后面。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>             [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>             [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 函数参数异常。<br>             [ARKUI_ERROR_CODE_ARKTS_NODE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 不支持对ArkTS创建的节点执行对应的操作。<br>             [ARKUI_ERROR_CODE_NODE_IS_ADOPTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 节点已被接纳为附属节点。从API version 22开始支持。|

### insertChildBefore()

```c
int32_t (*insertChildBefore)(ArkUI_NodeHandle parent, ArkUI_NodeHandle child, ArkUI_NodeHandle sibling)
```

**描述：**


将组件挂载到某个父节点之下，挂载位置在<b>sibling</b>节点之前。本接口属于节点操作接口，不建议在非主线程上调用。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) parent | 父节点指针。 |
|  [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) child | 子节点指针。 |
|  [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) sibling | 后一个兄弟节点指针，如果为空则插入位置在最后面。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>             [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>             [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 函数参数异常。<br>             [ARKUI_ERROR_CODE_ARKTS_NODE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 不支持对ArkTS创建的节点执行对应的操作。<br>             [ARKUI_ERROR_CODE_NODE_IS_ADOPTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 节点已被接纳为附属节点。从API version 22开始支持。 |

### insertChildAt()

```c
int32_t (*insertChildAt)(ArkUI_NodeHandle parent, ArkUI_NodeHandle child, int32_t position)
```

**描述：**


将组件挂载到某个父节点之下，挂载位置由<b>position</b>指定。本接口属于节点操作接口，不建议在非主线程上调用。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) parent | 父节点指针。 |
|  [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) child | 子节点指针。 |
| int32_t position | 父节点子节点列表中从0开始的插入位置，取值范围为[0, 当前子节点个数]；超出该范围时，默认插入到父节点末尾。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>             [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>             [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 函数参数异常。<br>             [ARKUI_ERROR_CODE_ARKTS_NODE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 不支持对ArkTS创建的节点执行对应的操作。<br>             [ARKUI_ERROR_CODE_NODE_IS_ADOPTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 节点已被接纳为附属节点。从API version 22开始支持。 |

### setAttribute()

```c
int32_t (*setAttribute)(ArkUI_NodeHandle node, ArkUI_NodeAttributeType attribute, const ArkUI_AttributeItem* item)
```

**描述：**


属性设置函数，不建议在非主线程上调用。

在实际业务场景下，如果组件设置的属性包含由开发者申请的堆内存，需确保组件不再使用后再调用对应释放接口。例如：[ArkUI_NodeAttributeType](capi-native-node-h.md#arkui_nodeattributetype)中的NODE_TEXT_CONTENT_WITH_STYLED_STRING。

**起始版本：** 12

**参数：**

| 参数项                                                                                | 描述 |
|------------------------------------------------------------------------------------| -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node                   | 需要设置属性的节点对象。 |
| [ArkUI_NodeAttributeType](capi-native-node-h.md#arkui_nodeattributetype) attribute | 需要设置的属性类型。 |
| const [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)* item  | 需要设置的属性值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>             [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>             [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 函数参数异常。<br>             [ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 组件不支持该属性。<br>             [ARKUI_ERROR_CODE_ARKTS_NODE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 不支持对ArkTS创建的节点执行对应的操作。<br>             [ARKUI_ERROR_CODE_ADAPTER_EXIST](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) NodeAdapter已经存在。 |

### getAttribute()

```c
const ArkUI_AttributeItem* (*getAttribute)(ArkUI_NodeHandle node, ArkUI_NodeAttributeType attribute)
```

**描述：**


属性获取函数。该接口返回的指针是ArkUI框架内部的缓冲区指针，不需要开发者主动调用delete释放内存，但是需要在该函数下一次被调用前使用，否则可能会被其他值所覆盖。

**起始版本：** 12

**参数：**

| 参数项                                                                                | 描述 |
|------------------------------------------------------------------------------------| -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node                   | 需要获取属性的节点对象。 |
| [ArkUI_NodeAttributeType](capi-native-node-h.md#arkui_nodeattributetype) attribute | 需要获取的属性类型。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| const [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)* | 当前属性类型的属性值，失败返回空指针。 |

### resetAttribute()

```c
int32_t (*resetAttribute)(ArkUI_NodeHandle node, ArkUI_NodeAttributeType attribute)
```

**描述：**


重置属性函数，不建议在非主线程上调用。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 需要重置属性的节点对象。 |
|  [ArkUI_NodeAttributeType](capi-native-node-h.md#arkui_nodeattributetype) attribute | 需要重置的属性类型。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>             [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>             [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 函数参数异常。<br>             [ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 组件不支持该属性。<br>             [ARKUI_ERROR_CODE_ARKTS_NODE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 不支持对ArkTS创建的节点执行对应的操作。 |

### registerNodeEvent()

```c
int32_t (*registerNodeEvent)(ArkUI_NodeHandle node, ArkUI_NodeEventType eventType, int32_t targetId, void* userData)
```

**描述：**


注册节点事件函数。事件触发后，可通过[addNodeEventReceiver](#addnodeeventreceiver)添加的组件级回调或[registerNodeEventReceiver](#registernodeeventreceiver)注册的全局回调接收；不再需要该事件时，可调用[unregisterNodeEvent](#unregisternodeevent)反注册。

**起始版本：** 12

**参数：**

| 参数项                                                                        | 描述                                                                                      |
|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node           | 需要注册事件的节点对象。                                                                            |
| [ArkUI_NodeEventType](capi-native-node-h.md#arkui_nodeeventtype) eventType | 需要注册的事件类型。                                                                              |
| int32_t targetId                                                           | 自定义事件ID，当事件触发时在回调参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) 中携带回来。 |
| void* userData                                                             | 自定义事件参数，当事件触发时在回调参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) 中携带回来。                                    |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>             [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>             [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 函数参数异常。<br>             [ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 组件不支持该事件。<br>             [ARKUI_ERROR_CODE_ARKTS_NODE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 不支持对ArkTS创建的节点执行对应的操作。 |

### unregisterNodeEvent()

```c
void (*unregisterNodeEvent)(ArkUI_NodeHandle node, ArkUI_NodeEventType eventType)
```

**描述：**


反注册此前通过[registerNodeEvent](#registernodeevent)注册的节点事件。反注册后，该事件不再触发相应回调。

**起始版本：** 12

**参数：**

| 参数项                                                              | 描述            |
|------------------------------------------------------------------|---------------|
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 需要反注册事件的节点对象。 |
| [ArkUI_NodeEventType](capi-native-node-h.md#arkui_nodeeventtype) eventType                                | 需要反注册的事件类型。              |

### registerNodeEventReceiver()

```c
void (*registerNodeEventReceiver)(void (*eventReceiver)(ArkUI_NodeEvent* event))
```

**描述：**


注册事件回调统一入口函数。ArkUI框架会统一收集过程中产生的组件事件并通过注册的eventReceiver函数回调给开发者。<br> 重复调用时会覆盖前一次注册的函数。<br> 避免直接保存[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象指针，数据会在回调结束后销毁。<br> 如果需要和组件实例绑定，可以使用[addNodeEventReceiver](#addnodeeventreceiver)函数接口。<br> 不再需要全局回调时，可调用[unregisterNodeEventReceiver](#unregisternodeeventreceiver)反注册。<br>

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
|-----|----|
| void (*eventReceiver)([ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)\* event) | 事件回调统一入口函数。   |

### unregisterNodeEventReceiver()

```c
void (*unregisterNodeEventReceiver)()
```

**描述：**


反注册通过[registerNodeEventReceiver](#registernodeeventreceiver)注册的全局事件回调统一入口函数。反注册后，全局入口不再接收组件事件。

**起始版本：** 12

### markDirty()

```c
void (*markDirty)(ArkUI_NodeHandle node, ArkUI_NodeDirtyFlag dirtyFlag)
```

**描述：**


强制标记当前节点需要重新测量、布局或绘制。系统属性更新时，ArkUI框架会自动标记节点并重新执行相应流程，无需开发者主动调用该函数；当开发者修改框架无法自动感知的自定义测量、布局或绘制数据时，可调用该函数触发对应流程。

**起始版本：** 12

**参数：**

| 参数项                                                                        | 描述           |
|----------------------------------------------------------------------------|--------------|
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node           | 需要重新测量、布局或绘制的节点对象。 |
| [ArkUI_NodeDirtyFlag](capi-native-node-h.md#arkui_nodedirtyflag) dirtyFlag | 指定重新执行的流程类型。  |

### getTotalChildCount()

```c
uint32_t (*getTotalChildCount)(ArkUI_NodeHandle node)
```

**描述：**


获取子节点的个数。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | 子节点的个数；如果没有子节点，则返回0。 |

### getChildAt()

```c
ArkUI_NodeHandle (*getChildAt)(ArkUI_NodeHandle node, int32_t position)
```

**描述：**


获取指定索引位置的子节点。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点对象。 |
|  int32_t position | 目标节点子节点列表中从0开始的索引，取值范围为[0, 子节点个数-1]；超出范围时返回NULL。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | 指定索引位置的子节点指针；如果该位置不存在子节点，则返回NULL。 |

### getFirstChild()

```c
ArkUI_NodeHandle (*getFirstChild)(ArkUI_NodeHandle node)
```

**描述：**


获取第一个子节点。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | 第一个子节点指针；如果没有子节点，则返回NULL。 |

### getLastChild()

```c
ArkUI_NodeHandle (*getLastChild)(ArkUI_NodeHandle node)
```

**描述：**


获取最后一个子节点。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | 最后一个子节点指针；如果没有子节点，则返回NULL。 |

### getPreviousSibling()

```c
ArkUI_NodeHandle (*getPreviousSibling)(ArkUI_NodeHandle node)
```

**描述：**


获取上一个兄弟节点。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | 上一个兄弟节点指针；如果不存在上一个兄弟节点，则返回NULL。 |

### getNextSibling()

```c
ArkUI_NodeHandle (*getNextSibling)(ArkUI_NodeHandle node)
```

**描述：**


获取下一个兄弟节点。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | 下一个兄弟节点指针；如果不存在下一个兄弟节点，则返回NULL。 |

### registerNodeCustomEvent()

```c
int32_t (*registerNodeCustomEvent)(ArkUI_NodeHandle node, ArkUI_NodeCustomEventType eventType, int32_t targetId, void* userData)
```

**描述：**


注册自定义节点事件函数。事件触发后，可通过[addNodeCustomEventReceiver](#addnodecustomeventreceiver)添加的组件级回调或[registerNodeCustomEventReceiver](#registernodecustomeventreceiver)注册的全局回调接收；不再需要该事件时，可调用[unregisterNodeCustomEvent](#unregisternodecustomevent)反注册。

**起始版本：** 12

**参数：**

| 参数项                                                                                    | 描述 |
|----------------------------------------------------------------------------------------| -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node                       | 需要注册事件的节点对象。 |
| [ArkUI_NodeCustomEventType](capi-native-node-node-attributes-custom-attributes-h.md#arkui_nodecustomeventtype) eventType | 需要注册的事件类型。 |
| int32_t targetId                                                                       | 自定义事件ID，当事件触发时在回调参数[ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md) 中携带回来。 |
| void* userData                                                                         | 自定义事件参数，当事件触发时在回调参数[ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md) 中携带回来。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>             [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>             [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 函数参数异常。<br>             [ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 组件不支持该事件。 |

### unregisterNodeCustomEvent()

```c
void (*unregisterNodeCustomEvent)(ArkUI_NodeHandle node, ArkUI_NodeCustomEventType eventType)
```

**描述：**


反注册此前通过[registerNodeCustomEvent](#registernodecustomevent)注册的自定义节点事件。反注册后，该事件不再触发相应回调。

**起始版本：** 12

**参数：**

| 参数项                                                                                    | 描述            |
|----------------------------------------------------------------------------------------|---------------|
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node                       | 需要反注册事件的节点对象。 |
| [ArkUI_NodeCustomEventType](capi-native-node-node-attributes-custom-attributes-h.md#arkui_nodecustomeventtype) eventType | 需要反注册的事件类型。              |

### registerNodeCustomEventReceiver()

```c
void (*registerNodeCustomEventReceiver)(void (*eventReceiver)(ArkUI_NodeCustomEvent* event))
```

**描述：**


注册自定义节点事件回调统一入口函数。ArkUI框架会统一收集过程中产生的自定义组件事件并通过注册的registerNodeCustomEventReceiver函数回调给开发者。<br> 重复调用时会覆盖前一次注册的函数。<br> 避免直接保存[ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)对象指针，数据会在回调结束后销毁。<br> 如果需要和组件实例绑定，可以使用[addNodeCustomEventReceiver](#addnodecustomeventreceiver)函数接口。<br> 不再需要全局回调时，可调用[unregisterNodeCustomEventReceiver](#unregisternodecustomeventreceiver)反注册。<br>

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
|-----|----|
| void (*eventReceiver)([ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)\* event)  | 事件回调统一入口函数。   |

### unregisterNodeCustomEventReceiver()

```c
void (*unregisterNodeCustomEventReceiver)()
```

**描述：**


反注册通过[registerNodeCustomEventReceiver](#registernodecustomeventreceiver)注册的全局自定义事件回调统一入口函数。反注册后，全局入口不再接收自定义组件事件。

**起始版本：** 12

### setMeasuredSize()

```c
int32_t (*setMeasuredSize)(ArkUI_NodeHandle node, int32_t width, int32_t height)
```

**描述：**


在测算回调函数中设置组件测算完成后的宽度和高度。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点对象。 |
|  int32_t width | 组件测算完成后的宽度，单位为px；小于0时按0处理。 |
|  int32_t height | 组件测算完成后的高度，单位为px；小于0时按0处理。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>             [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>             [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 函数参数异常。 |


### setLayoutPosition()

```c
int32_t (*setLayoutPosition)(ArkUI_NodeHandle node, int32_t positionX, int32_t positionY)
```

**描述：**

在布局回调函数中设置组件相对于父组件的布局位置。该接口优先级低于ArkUI_NodeAttributeType中的[NODE_POSITION](capi-native-node-h-nodeattributetype-layoutattributes.md#node_position)。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点对象。 |
|  int32_t positionX | 组件相对于父组件的X轴布局坐标，单位为px。 |
|  int32_t positionY | 组件相对于父组件的Y轴布局坐标，单位为px。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>             [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>             [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### getMeasuredSize()

```c
ArkUI_IntSize (*getMeasuredSize)(ArkUI_NodeHandle node)
```

**描述：**


获取组件测算完成后的宽高尺寸。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点对象。 |

**返回：**

| 类型                | 说明 |
|-------------------| -- |
| [ArkUI_IntSize](capi-arkui-nativemodule-arkui-intsize.md) | ArkUI_IntSize 组件的宽高。 |

### getLayoutPosition()

```c
ArkUI_IntOffset (*getLayoutPosition)(ArkUI_NodeHandle node)
```

**描述：**

获取组件布局完成后该节点相对于父节点的偏移，单位为px。该偏移是父容器对该节点进行布局之后的结果，因此布局之后生效的offset属性和不参与布局的position属性不影响该偏移值。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点对象。 |

**返回：**

| 类型                  | 说明 |
|---------------------| -- |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md) | 组件布局完成后相对于父节点的偏移，单位为px。 |

### measureNode()

```c
int32_t (*measureNode)(ArkUI_NodeHandle node, ArkUI_LayoutConstraint* Constraint)
```

**描述：**


对目标组件进行测算，可以通过getMeasuredSize接口获取测算后的大小。

**起始版本：** 12

**参数：**

| 参数项                                                              | 描述 |
|------------------------------------------------------------------| -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点对象。 |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint                           | 目标组件测算时使用的尺寸约束，约束值单位为px。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>             [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>             [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### layoutNode()

```c
int32_t (*layoutNode)(ArkUI_NodeHandle node, int32_t positionX, int32_t positionY)
```

**描述：**


对目标组件进行布局并传递该组件相对父组件的期望位置。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点对象。 |
|  int32_t positionX | 目标组件相对于父组件的X轴期望坐标，单位为px。 |
|  int32_t positionY | 目标组件相对于父组件的Y轴期望坐标，单位为px。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>             [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>             [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### addNodeEventReceiver()

```c
int32_t (*addNodeEventReceiver)(ArkUI_NodeHandle node, void (*eventReceiver)(ArkUI_NodeEvent* event))
```

**描述：**


在组件上添加组件事件回调函数，用于接收该组件产生的组件事件。不同于registerNodeEventReceiver的全局注册函数，该函数允许在同一个组件上添加多个事件接收器。<br> 该函数添加的监听回调函数触发时机会先于registerNodeEventReceiver注册的全局回调函数。<br> 避免直接保存[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象指针，数据会在回调结束后销毁。<br> 不再需要该回调时，可调用[removeNodeEventReceiver](#removenodeeventreceiver)删除。<br>

**起始版本：** 12

**参数：**

| 参数项                                                              | 描述 |
|------------------------------------------------------------------| -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 用于添加组件事件回调函数的对象。 |
| void (*eventReceiver)([ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)\* event)                    | 组件事件回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>             [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>             [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### removeNodeEventReceiver()

```c
int32_t (*removeNodeEventReceiver)(ArkUI_NodeHandle node, void (*eventReceiver)(ArkUI_NodeEvent* event))
```

**描述：**


删除此前通过[addNodeEventReceiver](#addnodeeventreceiver)添加到该组件的事件回调函数。删除后，该回调不再接收该组件产生的事件。

**起始版本：** 12

**参数：**

| 参数项                                                              | 描述 |
|------------------------------------------------------------------| -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 用于删除组件事件回调函数的对象。 |
| void (\*eventReceiver)([ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)\* event)                    | 待删除的组件事件回调函数，必须与调用[addNodeEventReceiver](#addnodeeventreceiver)时传入的函数指针相同。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>             [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>             [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### addNodeCustomEventReceiver()

```c
int32_t (*addNodeCustomEventReceiver)(ArkUI_NodeHandle node, void (*eventReceiver)(ArkUI_NodeCustomEvent* event))
```

**描述：**


在组件上添加自定义事件回调函数，用于接收该组件产生的自定义事件（如布局事件、绘制事件）。不同于registerNodeCustomEventReceiver的全局注册函数，该函数允许在同一个组件上添加多个事件接收器。<br> 该函数添加的监听回调函数触发时机会先于registerNodeCustomEventReceiver注册的全局回调函数。<br> 避免直接保存[ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)对象指针，数据会在回调结束后销毁。<br> 不再需要该回调时，可调用[removeNodeCustomEventReceiver](#removenodecustomeventreceiver)删除。<br>

**起始版本：** 12

**参数：**

| 参数项                                                              | 描述 |
|------------------------------------------------------------------| -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 用于添加组件自定义事件回调函数的对象。 |
| void (*eventReceiver)([ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)\* event)              | 组件自定义事件回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>             [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>             [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### removeNodeCustomEventReceiver()

```c
int32_t (*removeNodeCustomEventReceiver)(ArkUI_NodeHandle node, void (*eventReceiver)(ArkUI_NodeCustomEvent* event))
```

**描述：**


删除此前通过[addNodeCustomEventReceiver](#addnodecustomeventreceiver)添加到该组件的自定义事件回调函数。删除后，该回调不再接收该组件产生的自定义事件。

**起始版本：** 12

**参数：**

| 参数项                                                              | 描述 |
|------------------------------------------------------------------| -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 用于删除组件自定义事件回调函数的对象。 |
| void (\*eventReceiver)([ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)\* event)              | 待删除的组件自定义事件回调函数，必须与调用[addNodeCustomEventReceiver](#addnodecustomeventreceiver)时传入的函数指针相同。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>             [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>             [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### setUserData()

```c
int32_t (*setUserData)(ArkUI_NodeHandle node, void* userData)
```

**描述：**


在组件上保存自定义数据。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 用于保存自定义数据的组件。 |
|  void* userData | 要保存的自定义数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>             [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>             [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### getUserData()

```c
void* (*getUserData)(ArkUI_NodeHandle node)
```

**描述：**


获取在组件上保存的自定义数据。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 保存了自定义数据的组件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| void* | 此前通过[setUserData](#setuserdata)保存在该组件上的自定义数据指针。 |

### setLengthMetricUnit()

```c
int32_t (*setLengthMetricUnit)(ArkUI_NodeHandle node, ArkUI_LengthMetricUnit unit)
```

**描述：**


指定组件通过Native Node API设置长度类属性时使用的单位。当业务需要统一使用px、vp或fp设置组件长度类属性时，可调用本接口指定单位。

**起始版本：** 12

**参数：**

| 参数项                                                                         | 描述 |
|-----------------------------------------------------------------------------| -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node            | 用于指定单位的组件。 |
| [ArkUI_LengthMetricUnit](capi-native-type-h.md#arkui_lengthmetricunit) unit | 组件长度类属性的单位类型。默认值为ARKUI_LENGTH_METRIC_UNIT_DEFAULT；使用默认值时，字体类属性单位为fp，非字体类属性单位为vp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>             [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>             [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### getParent()

```c
ArkUI_NodeHandle (*getParent)(ArkUI_NodeHandle node)
```

**描述：**


获取父节点。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | 父节点指针；如果不存在父节点，则返回NULL。 |

### removeAllChildren()

```c
int32_t (*removeAllChildren)(ArkUI_NodeHandle parent)
```

**描述：**


从父组件上卸载所有子节点。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) parent | 父节点指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>             [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>             [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 函数参数异常。 |
