# content_embed_extension.h
<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @weiguoning-->
<!--Designer: @zhuwei-->
<!--Tester: @zhaotianyu-->
<!--Adviser: @jinqiuheng-->

## 概述

定义OE Extension相关数据结构和操作接口。

**引用文件：** <ContentEmbedKit/content_embed/content_embed_extension.h>

**库：** libcontent_embed_ndk.so

**系统能力：** SystemCapability.ContentEmbed.ObjectEditor

**起始版本：** 24

**相关模块：** [ContentEmbed](capi-contentembed.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ContentEmbed_ExtensionContext](capi-contentembed-contentembed-extensioncontext.md) | ContentEmbed_ExtensionContext | 声明OE Extension上下文的结构体类型。 |
| [ContentEmbed_ExtensionContext*](capi-contentembed-contentembed-extensioncontext8h.md) | ContentEmbed_ExtensionContextHandle | 声明OE Extension上下文对象指针类型。 |
| [ContentEmbed_ExtensionInstance](capi-contentembed-contentembed-extensioninstance.md) | ContentEmbed_ExtensionInstance | 声明OE Extension实例的结构体类型。表示一个OE Extension实例，管理扩展的生命周期、回调注册和对象关联等核心功能。 |
| [ContentEmbed_ExtensionInstance*](capi-contentembed-contentembed-extensioninstance8h.md) | ContentEmbed_ExtensionInstanceHandle | 声明OE Extension实例对象指针类型。 |
| [ContentEmbed_Object](capi-contentembed-contentembed-object.md) | ContentEmbed_Object | 声明ContentEmbed_Object结构体类型。表示一个OE文档对象在服务端封装的OE对象，用于与客户端OE对象交互。 |
| [ContentEmbed_Object*](capi-contentembed-contentembed-object8h.md) | ContentEmbed_ObjectHandle | 声明ContentEmbed_Object对象指针类型。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContentEmbedContext(ContentEmbed_ExtensionInstanceHandle ceInstance, ContentEmbed_ExtensionContextHandle *ceContext)](#oh_contentembed_extension_getcontentembedcontext) | - | 从OE Extension实例中获取其对应的上下文对象。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContext(ContentEmbed_ExtensionContextHandle ceContext, AbilityRuntime_ContextHandle *context)](#oh_contentembed_extension_getcontext) | - | 从OE Extension上下文中获取AbilityRuntime上下文。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetExtensionInstance(AbilityRuntime_ExtensionInstanceHandle baseInstance, ContentEmbed_ExtensionInstanceHandle *ceInstance)](#oh_contentembed_extension_getextensioninstance) | - | 从AbilityRuntime ExtensionAbility实例中获取OE Extension实例。 |
| [typedef void (\*OH_ContentEmbed_Extension_OnCreateFunc)(ContentEmbed_ExtensionInstanceHandle instance, AbilityBase_Want *want)](#oh_contentembed_extension_oncreatefunc) | OH_ContentEmbed_Extension_OnCreateFunc | OE Extension实例创建时的生命周期函数类型。当OE Extension实例创建完成时调用此生命周期函数，用于执行初始化操作。开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeroncreatefunc)注册到OE Extension实例。 |
| [typedef void (\*OH_ContentEmbed_Extension_OnDestroyFunc)(ContentEmbed_ExtensionInstanceHandle instance)](#oh_contentembed_extension_ondestroyfunc) | OH_ContentEmbed_Extension_OnDestroyFunc | OE Extension实例销毁时的生命周期函数类型。当OE Extension实例即将销毁时调用此生命周期函数，用于执行资源释放和清理操作。开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondestroyfunc)注册到OE Extension实例。 |
| [typedef void (\*OH_ContentEmbed_Extension_OnObjectAttachFunc)(ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_onobjectattachfunc) | OH_ContentEmbed_Extension_OnObjectAttachFunc | 当客户端OE对象连接到OE Extension实例时触发此回调函数，用于执行服务端OE对象关联后的初始化操作。开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectattachfunc)注册到OE Extension实例。 |
| [typedef void (\*OH_ContentEmbed_Extension_OnObjectDetachFunc)(ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_onobjectdetachfunc) | OH_ContentEmbed_Extension_OnObjectDetachFunc | 当客户端OE对象从OE Extension实例断开连接时触发此回调函数，用于执行服务端OE对象断开连接后的清理操作。开发者需要实现此函数并通过 [OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectdetachfunc)注册到OE Extension实例。 |
| [typedef void (\*OH_ContentEmbed_Extension_OnWriteToDataStreamFunc)(ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_onwritetodatastreamfunc) | OH_ContentEmbed_Extension_OnWriteToDataStreamFunc | 当服务端OE对象写入OE文档数据流时的回调函数类型。开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronwritetodatastreamfunc)注册到服务端OE对象。 |
| [typedef void (\*OH_ContentEmbed_Extension_OnGetSnapshotFunc)(ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_ongetsnapshotfunc) | OH_ContentEmbed_Extension_OnGetSnapshotFunc | 当客户端OE对象请求获取OE文档快照时的回调函数类型。开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetsnapshotfunc)注册到服务端OE对象。 |
| [typedef void (\*OH_ContentEmbed_Extension_OnDoEditFunc)(ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_ondoeditfunc) | OH_ContentEmbed_Extension_OnDoEditFunc | 当客户端OE对象请求编辑OE文档时的回调函数类型。开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondoeditfunc)注册到服务端OE对象。 |
| [typedef void (\*OH_ContentEmbed_Extension_OnGetEditStatusFunc)(ContentEmbed_ObjectHandle object, bool *isEditing, bool *isModified)](#oh_contentembed_extension_ongeteditstatusfunc) | OH_ContentEmbed_Extension_OnGetEditStatusFunc | 当客户端OE对象请求OE文档编辑状态时的回调函数类型。开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongeteditstatusfunc)注册到服务端OE对象。 |
| [typedef void (\*OH_ContentEmbed_Extension_OnGetCapabilityFunc)(ContentEmbed_ObjectHandle object, uint32_t *bitmask)](#oh_contentembed_extension_ongetcapabilityfunc) | OH_ContentEmbed_Extension_OnGetCapabilityFunc | 当客户端OE对象请求OE Extension支持能力时的回调函数类型。开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetcapabilityfunc)注册到服务端OE对象。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnCreateFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnCreateFunc onCreateFunc)](#oh_contentembed_extension_registeroncreatefunc) | - | 注册OE Extension实例创建时的生命周期函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnDestroyFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnDestroyFunc onDestroyFunc)](#oh_contentembed_extension_registerondestroyfunc) | - | 注册OE Extension实例销毁时的生命周期函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnObjectAttachFunc onObjectAttachFunc)](#oh_contentembed_extension_registeronobjectattachfunc) | - | 注册客户端OE对象连接时的回调函数。可以通过调用[OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_unregisteronobjectattachfunc)取消注册。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc(ContentEmbed_ExtensionInstanceHandle instance)](#oh_contentembed_extension_unregisteronobjectattachfunc) | - | 取消OE Extension实例中已注册的客户端OE对象连接事件回调函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnObjectDetachFunc onObjectDetachFunc)](#oh_contentembed_extension_registeronobjectdetachfunc) | - | 注册服务端OE对象断开连接时的回调函数。可以通过调用[OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_unregisteronobjectdetachfunc)取消注册。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc(ContentEmbed_ExtensionInstanceHandle instance)](#oh_contentembed_extension_unregisteronobjectdetachfunc) | - | 取消OE Extension实例中已注册的OE对象断开连接事件回调函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnWriteToDataStreamFunc onWriteToDataStreamFunc)](#oh_contentembed_extension_registeronwritetodatastreamfunc) | - | 注册服务端OE对象写入OE文档数据流时的回调函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetSnapshotFunc onGetSnapshotFunc)](#oh_contentembed_extension_registerongetsnapshotfunc) | - | 注册客户端OE对象请求获取OE文档快照时的回调函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnDoEditFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnDoEditFunc onDoEditFunc)](#oh_contentembed_extension_registerondoeditfunc) | - | 注册客户端OE对象请求编辑OE文档时的回调函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetEditStatusFunc onGetEditStatusFunc)](#oh_contentembed_extension_registerongeteditstatusfunc) | - | 注册客户端OE对象OE文档请求编辑状态时的回调函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetCapabilityFunc onGetCapabilityFunc)](#oh_contentembed_extension_registerongetcapabilityfunc) | - | 注册客户端OE对象请求支持能力时的回调函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContentEmbedDocument(ContentEmbed_ObjectHandle object, ContentEmbed_Document **ceDocument)](#oh_contentembed_extension_getcontentembeddocument) | - | 获取OE对象关联的OE文档实例。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnUpdate(ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_callbacktoonupdate) | - | 触发客户端OE对象注册的OE文档更新回调函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnError(ContentEmbed_ObjectHandle object, ContentEmbed_ErrorCode code)](#oh_contentembed_extension_callbacktoonerror) | - | 触发客户端OE对象注册的OE文档错误回调函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnEditingFinished(ContentEmbed_ObjectHandle object, bool dataModified)](#oh_contentembed_extension_callbacktooneditingfinished) | - | 触发客户端OE对象注册的OE文档编辑完成回调函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnExtensionStopped(ContentEmbed_ExtensionInstanceHandle instance)](#oh_contentembed_extension_callbacktoonextensionstopped) | - | 触发客户端OE对象注册的OE Extension停止回调函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_SetSnapshot(ContentEmbed_ObjectHandle object, OH_PixelmapNative *pixelMap)](#oh_contentembed_extension_setsnapshot) | - | 设置客户端OE对象关联的OE文档快照图像。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextStartSelfUIAbility(ContentEmbed_ExtensionContextHandle context, AbilityBase_Want *want)](#oh_contentembed_extension_contextstartselfuiability) | - | 通过OE Extension上下文启动自身的UIAbility。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions(ContentEmbed_ExtensionContextHandle context, AbilityBase_Want *want, AbilityRuntime_StartOptions *options)](#oh_contentembed_extension_contextstartselfuiabilitywithstartoptions) | - | 使用启动选项启动OE Extension上下文自身的UIAbility。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextTerminateAbility(ContentEmbed_ExtensionContextHandle context)](#oh_contentembed_extension_contextterminateability) | - | 终止OE Extension上下文自身的UIAbility。 |

## 函数说明

### OH_ContentEmbed_Extension_GetContentEmbedContext()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContentEmbedContext(ContentEmbed_ExtensionInstanceHandle ceInstance, ContentEmbed_ExtensionContextHandle *ceContext)
```

**描述**

从OE Extension实例中获取其对应的上下文对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) ceInstance | OE Extension实例对象的指针。 |
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) *ceContext | 输出参数。调用成功后，该指针指向OE Extension实例的上下文对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_GetContext()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContext(ContentEmbed_ExtensionContextHandle ceContext, AbilityRuntime_ContextHandle *context)
```

**描述**

从OE Extension上下文中获取AbilityRuntime上下文。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) ceContext | OE Extension上下文对象的指针。 |
| [AbilityRuntime_ContextHandle](../apis-ability-kit/capi-abilityruntime-abilityruntime-context8h.md) *context | 输出参数。调用成功后，该指针指向AbilityRuntime上下文对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_GetExtensionInstance()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetExtensionInstance(AbilityRuntime_ExtensionInstanceHandle baseInstance, ContentEmbed_ExtensionInstanceHandle *ceInstance)
```

**描述**

从AbilityRuntime ExtensionAbility实例中获取OE Extension实例。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [AbilityRuntime_ExtensionInstanceHandle](../apis-ability-kit/capi-abilityruntime-extensioninstance8h.md) baseInstance | AbilityRuntime_ExtensionInstance实例的指针。 |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) *ceInstance | 输出参数。调用成功后，该指针指向OE Extension实例对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_OnCreateFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnCreateFunc)(ContentEmbed_ExtensionInstanceHandle instance, AbilityBase_Want *want)
```

**描述**

OE Extension实例创建时的生命周期函数类型。当OE Extension实例创建完成时调用此生命周期函数，用于执行初始化操作。开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeroncreatefunc)注册到OE Extension实例。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | OE Extension实例对象的指针。 |
| [AbilityBase_Want](../apis-ability-kit/capi-abilitybase-want.md) \*want | AbilityBase_Want实例的指针。 |

### OH_ContentEmbed_Extension_OnDestroyFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnDestroyFunc)(ContentEmbed_ExtensionInstanceHandle instance)
```

**描述**

OE Extension实例销毁时的生命周期函数类型。当OE Extension实例即将销毁时调用此生命周期函数，用于执行资源释放和清理操作。开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondestroyfunc)注册到OE Extension实例。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | OE Extension实例对象的指针。 |

### OH_ContentEmbed_Extension_OnObjectAttachFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnObjectAttachFunc)(ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object)
```

**描述**

当客户端OE对象连接到OE Extension实例时触发此回调函数，用于执行服务端OE对象关联后的初始化操作。开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectattachfunc)注册到OE Extension实例。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioncontext8h.md) instance | OE Extension实例对象的指针。 |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | ContentEmbed_Object对象指针。 |

### OH_ContentEmbed_Extension_OnObjectDetachFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnObjectDetachFunc)(ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object)
```

**描述**

当客户端OE对象从OE Extension实例断开连接时触发此回调函数，用于执行服务端OE对象断开连接后的清理操作。开发者需要实现此函数并通过 [OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectdetachfunc)注册到OE Extension实例。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | OE Extension实例对象的指针。 |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | ContentEmbed_Object对象指针。 |

### OH_ContentEmbed_Extension_OnWriteToDataStreamFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnWriteToDataStreamFunc)(ContentEmbed_ObjectHandle object)
```

**描述**

当服务端OE对象写入OE文档数据流时的回调函数类型。开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronwritetodatastreamfunc)注册到服务端OE对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | ContentEmbed_Object对象指针。 |

### OH_ContentEmbed_Extension_OnGetSnapshotFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnGetSnapshotFunc)(ContentEmbed_ObjectHandle object)
```

**描述**

当客户端OE对象请求获取OE文档快照时的回调函数类型。开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetsnapshotfunc)注册到服务端OE对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | ContentEmbed_Object对象指针。 |

### OH_ContentEmbed_Extension_OnDoEditFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnDoEditFunc)(ContentEmbed_ObjectHandle object)
```

**描述**

当客户端OE对象请求编辑OE文档时的回调函数类型。开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondoeditfunc)注册到服务端OE对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | ContentEmbed_Object对象指针。 |

### OH_ContentEmbed_Extension_OnGetEditStatusFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnGetEditStatusFunc)(ContentEmbed_ObjectHandle object, bool *isEditing, bool *isModified)
```

**描述**

当客户端OE对象请求OE文档编辑状态时的回调函数类型。开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongeteditstatusfunc)注册到服务端OE对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | ContentEmbed_Object对象指针。 |
| bool \*isEditing | 输出参数，表示OE文档是否正在编辑。 |
| bool \*isModified | 输出参数，表示OE文档是否已被修改。 |

### OH_ContentEmbed_Extension_OnGetCapabilityFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnGetCapabilityFunc)(ContentEmbed_ObjectHandle object, uint32_t *bitmask)
```

**描述**

当客户端OE对象请求OE Extension支持能力时的回调函数类型。开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetcapabilityfunc)注册到服务端OE对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | ContentEmbed_Object对象指针。 |
| uint32_t \*bitmask | 输出参数，表示OE Extension实例支持的能力，由[ContentEmbed_CapabilityCode](capi-content-embed-common-h.md#contentembed_capabilitycode)中的值组合而成。 |

### OH_ContentEmbed_Extension_RegisterOnCreateFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnCreateFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnCreateFunc onCreateFunc)
```

**描述**

注册OE Extension实例创建时的生命周期函数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | 指向OE Extension实例对象的指针。 |
| [OH_ContentEmbed_Extension_OnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_oncreatefunc) onCreateFunc | 要注册的[OH_ContentEmbed_Extension_OnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_oncreatefunc)生命周期函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_RegisterOnDestroyFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnDestroyFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnDestroyFunc onDestroyFunc)
```

**描述**

注册OE Extension实例销毁时的生命周期函数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | 指向OE Extension实例对象的指针。 |
| [OH_ContentEmbed_Extension_OnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ondestroyfunc) onDestroyFunc | 要注册的[OH_ContentEmbed_Extension_OnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ondestroyfunc)生命周期函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnObjectAttachFunc onObjectAttachFunc)
```

**描述**

注册客户端OE对象连接时的回调函数。可以通过调用[OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_unregisteronobjectattachfunc)取消注册。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | 指向OE Extension实例对象的指针。 |
| [OH_ContentEmbed_Extension_OnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onobjectattachfunc) onObjectAttachFunc | 要注册的[OH_ContentEmbed_Extension_OnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onobjectattachfunc)回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc(ContentEmbed_ExtensionInstanceHandle instance)
```

**描述**

取消OE Extension实例中已注册的客户端OE对象连接事件回调函数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | 指向OE Extension实例对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnObjectDetachFunc onObjectDetachFunc)
```

**描述**

注册服务端OE对象断开连接时的回调函数。可以通过调用[OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_unregisteronobjectdetachfunc)取消注册。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | 指向OE Extension实例对象的指针。 |
| [OH_ContentEmbed_Extension_OnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onobjectdetachfunc) onObjectDetachFunc | 要注册的[OH_ContentEmbed_Extension_OnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onobjectdetachfunc)回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败，可能是instance无效。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc(ContentEmbed_ExtensionInstanceHandle instance)
```

**描述**

取消注册OE对象断开连接时的回调函数。取消OE Extension实例中已注册的OE对象断开连接事件回调函数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | 指向OE Extension实例对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnWriteToDataStreamFunc onWriteToDataStreamFunc)
```

**描述**

注册服务端OE对象写入OE文档数据流时的回调函数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | 指向ContentEmbed_Object对象指针。 |
| [OH_ContentEmbed_Extension_OnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onwritetodatastreamfunc) onWriteToDataStreamFunc | 要注册的[OH_ContentEmbed_Extension_OnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onwritetodatastreamfunc)回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetSnapshotFunc onGetSnapshotFunc)
```

**描述**

注册客户端OE对象请求获取OE文档快照时的回调函数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | 指向ContentEmbed_Object对象指针。 |
| [OH_ContentEmbed_Extension_OnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongetsnapshotfunc) onGetSnapshotFunc | 要注册的[OH_ContentEmbed_Extension_OnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongetsnapshotfunc)回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_RegisterOnDoEditFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnDoEditFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnDoEditFunc onDoEditFunc)
```

**描述**

注册客户端OE对象请求编辑OE文档时的回调函数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | 指向ContentEmbed_Object对象指针。 |
| [OH_ContentEmbed_Extension_OnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ondoeditfunc) onDoEditFunc | 要注册的[OH_ContentEmbed_Extension_OnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ondoeditfunc)回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetEditStatusFunc onGetEditStatusFunc)
```

**描述**

注册客户端OE对象OE文档请求编辑状态时的回调函数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | 指向ContentEmbed_Object对象指针。 |
| [OH_ContentEmbed_Extension_OnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongeteditstatusfunc) onGetEditStatusFunc | 要注册的[OH_ContentEmbed_Extension_OnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongeteditstatusfunc)回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetCapabilityFunc onGetCapabilityFunc)
```

**描述**

注册客户端OE对象请求支持能力时的回调函数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | 指向ContentEmbed_Object对象指针。 |
| [OH_ContentEmbed_Extension_OnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongetcapabilityfunc) onGetCapabilityFunc | 要注册的[OH_ContentEmbed_Extension_OnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongetcapabilityfunc)回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_GetContentEmbedDocument()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContentEmbedDocument(ContentEmbed_ObjectHandle object, ContentEmbed_Document **ceDocument)
```

**描述**

获取OE对象关联的OE文档实例。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | 指向ContentEmbed_Object对象指针。 |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) **ceDocument | 输出参数，用于存储OE文档实例的指针。调用成功后，该指针指向关联的OE文档实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_CallbackToOnUpdate()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnUpdate(ContentEmbed_ObjectHandle object)
```

**描述**

触发客户端OE对象注册的OE文档更新回调函数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | 指向ContentEmbed_Object对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED](capi-content-embed-common-h.md#contentembed_errorcode)表示客户端回调未注册。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_CLIENT_CALLBACK_FAILED](capi-content-embed-common-h.md#contentembed_errorcode)表示客户端回调执行失败。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_CallbackToOnError()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnError(ContentEmbed_ObjectHandle object, ContentEmbed_ErrorCode code)
```

**描述**

触发客户端OE对象注册的OE文档错误回调函数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | 指向ContentEmbed_Object对象指针。 |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) code | 表示错误码，详细定义参见[ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED](capi-content-embed-common-h.md#contentembed_errorcode)表示客户端回调未注册。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_CLIENT_CALLBACK_FAILED](capi-content-embed-common-h.md#contentembed_errorcode)表示客户端回调执行失败。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_CallbackToOnEditingFinished()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnEditingFinished(ContentEmbed_ObjectHandle object, bool dataModified)
```

**描述**

触发客户端OE对象注册的OE文档编辑完成回调函数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | 指向ContentEmbed_Object对象指针。 |
| bool dataModified | 表示文档数据是否已被修改，true表示有修改，false表示无修改。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED](capi-content-embed-common-h.md#contentembed_errorcode)表示客户端回调未注册。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_CLIENT_CALLBACK_FAILED](capi-content-embed-common-h.md#contentembed_errorcode)表示客户端回调执行失败。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_CallbackToOnExtensionStopped()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnExtensionStopped(ContentEmbed_ExtensionInstanceHandle instance)
```

**描述**

触发客户端OE对象注册的OE Extension停止回调函数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | 指向OE Extension实例对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED](capi-content-embed-common-h.md#contentembed_errorcode)表示客户端回调未注册。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_CLIENT_CALLBACK_FAILED](capi-content-embed-common-h.md#contentembed_errorcode)表示客户端回调执行失败。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_SetSnapshot()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_SetSnapshot(ContentEmbed_ObjectHandle object, OH_PixelmapNative *pixelMap)
```

**描述**

设置客户端OE对象关联的OE文档快照图像。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | 指向ContentEmbed_Object对象指针。 |
| [OH_PixelmapNative](../apis-arkgraphics2d/capi-drawing-oh-pixelmapnative.md) *pixelMap | 文档快照的像素图对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IMAGE_PACKER_OPERATION_FAILED](capi-content-embed-common-h.md#contentembed_errorcode)表示图像打包操作失败。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_ContextStartSelfUIAbility()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextStartSelfUIAbility(ContentEmbed_ExtensionContextHandle context, AbilityBase_Want *want)
```

**描述**

通过OE Extension上下文启动自身的UIAbility。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) context | 指向OE Extension上下文对象的指针。 |
| [AbilityBase_Want](../apis-ability-kit/capi-abilitybase-want.md) *want | 启动UIAbility时传递的参数，包含目标组件信息和自定义数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_SYSTEM_ABNORMAL](capi-content-embed-common-h.md#contentembed_errorcode)表示系统服务异常。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions(ContentEmbed_ExtensionContextHandle context, AbilityBase_Want *want, AbilityRuntime_StartOptions *options)
```

**描述**

使用启动选项启动OE Extension上下文自身的UIAbility。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) context | 指向OE Extension上下文对象的指针。 |
| [AbilityBase_Want](../apis-ability-kit/capi-abilitybase-want.md) *want | 启动UIAbility时传递的参数，包含目标组件信息和自定义数据。 |
| [AbilityRuntime_StartOptions](../apis-ability-kit/capi-abilityruntime-startoptions.md) *options | 启动UIAbility时的附加选项。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_SYSTEM_ABNORMAL](capi-content-embed-common-h.md#contentembed_errorcode)表示系统服务异常。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_ContextTerminateAbility()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextTerminateAbility(ContentEmbed_ExtensionContextHandle context)
```

**描述**

终止OE Extension上下文自身的UIAbility。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) context | 指向OE Extension上下文对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_SYSTEM_ABNORMAL](capi-content-embed-common-h.md#contentembed_errorcode)表示系统服务异常。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |
