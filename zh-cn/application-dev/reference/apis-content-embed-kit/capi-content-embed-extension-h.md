# content_embed_extension.h

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->

## 概述

定义服务端应用OE Extension相关数据结构和操作接口，提供OE Extension实例生命周期管理、客户端OE对象关联与回调注册、快照获取及编辑操作等能力，适用于在服务端处理文档嵌入与编辑场景。

**引用文件：** <ContentEmbedKit/content_embed/content_embed_extension.h>

**库：** libcontent_embed_ndk.so

**系统能力：** SystemCapability.ContentEmbed.ObjectEditor

**起始版本：** 24

**相关模块：** [ContentEmbed](capi-contentembed.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) | ContentEmbed_Document | 声明OE文档结构体类型。封装了被嵌入文档的元数据、内容和存储结构，用于在应用中统一管理嵌入文档的数据，便于对嵌入文档进行访问、解析与存储。<br>开发者可根据数据来源选取：<br>拥有OEID时使用[OH_ContentEmbed_CreateDocumentByOEid](capi-content-embed-document-h.md#oh_contentembed_createdocumentbyoeid)；<br>拥有源文件并需嵌入/链接时使用[OH_ContentEmbed_CreateDocumentByFile](capi-content-embed-document-h.md#oh_contentembed_createdocumentbyfile)；<br>拥有已保存的OE格式文件时使用[OH_ContentEmbed_LoadDocumentFromFile](capi-content-embed-document-h.md#oh_contentembed_loaddocumentfromfile)。 |
| [ContentEmbed_ExtensionContext](capi-contentembed-contentembed-extensioncontext.md) | ContentEmbed_ExtensionContext | 声明OE Extension上下文的结构体类型。 |
| [ContentEmbed_ExtensionContext*](capi-contentembed-contentembed-extensioncontext8h.md) | ContentEmbed_ExtensionContextHandle | 声明OE Extension上下文对象指针类型。该指针对象用于在ContentEmbed Extension流程中承载和管理OE Extension的运行上下文信息。<br>可通过[OH_ContentEmbed_Extension_GetContentEmbedContext](capi-content-embed-extension-h.md#oh_contentembed_extension_getcontentembedcontext)从OE Extension实例获取，支持通过[OH_ContentEmbed_Extension_GetContext](capi-content-embed-extension-h.md#oh_contentembed_extension_getcontext)获取AbilityRuntime上下文、[OH_ContentEmbed_Extension_ContextStartSelfUIAbility](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiability)或[OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiabilitywithstartoptions)启动自身UIAbility及[OH_ContentEmbed_Extension_ContextTerminateAbility](capi-content-embed-extension-h.md#oh_contentembed_extension_contextterminateability)销毁OE Extension等操作。 |
| [ContentEmbed_ExtensionInstance](capi-contentembed-contentembed-extensioninstance.md) | ContentEmbed_ExtensionInstance | 声明OE Extension实例的结构体类型。管理扩展的生命周期、回调注册和客户端OE对象关联等核心功能。适用于服务端应用需要嵌入OE扩展能力并完成扩展与客户端OE文档之间生命周期同步、回调监听及对象关联绑定的场景。 |
| [ContentEmbed_ExtensionInstance*](capi-contentembed-contentembed-extensioninstance8h.md) | ContentEmbed_ExtensionInstanceHandle | 声明OE Extension实例对象指针类型。需要在OH_AbilityRuntime_OnNativeExtensionCreate函数实现里通过[OH_ContentEmbed_Extension_GetExtensionInstance](capi-content-embed-extension-h.md#oh_contentembed_extension_getextensioninstance)方法，在OE Extension被系统启动时获取OE Extension实例对象。 |
| [ContentEmbed_Object](capi-contentembed-contentembed-object.md) | ContentEmbed_Object | 声明ContentEmbed_Object结构体类型。用于指向OE文档在服务端封装的文档嵌入和编辑的程序对象（简称服务端OE对象）。 |
| [ContentEmbed_Object*](capi-contentembed-contentembed-object8h.md) | ContentEmbed_ObjectHandle | 声明ContentEmbed_Object对象指针类型。当客户端连接服务端时，系统创建该对象实例，并回调[OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectattachfunc)注册的OH_ContentEmbed_Extension_OnObjectAttachFunc函数，并传入该类型的实例指针。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContentEmbedContext(ContentEmbed_ExtensionInstanceHandle ceInstance, ContentEmbed_ExtensionContextHandle *ceContext)](#oh_contentembed_extension_getcontentembedcontext) | - | 从OE Extension实例中获取其对应的OE Extension上下文对象。支持通过[OH_ContentEmbed_Extension_GetContext](capi-content-embed-extension-h.md#oh_contentembed_extension_getcontext)获取AbilityRuntime上下文、[OH_ContentEmbed_Extension_ContextStartSelfUIAbility](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiability)或[OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiabilitywithstartoptions)启动自身UIAbility及[OH_ContentEmbed_Extension_ContextTerminateAbility](capi-content-embed-extension-h.md#oh_contentembed_extension_contextterminateability)销毁OE Extension等操作。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContext(ContentEmbed_ExtensionContextHandle ceContext, AbilityRuntime_ContextHandle *context)](#oh_contentembed_extension_getcontext) | - | 从OE Extension上下文中获取AbilityRuntime上下文。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetExtensionInstance(AbilityRuntime_ExtensionInstanceHandle baseInstance, ContentEmbed_ExtensionInstanceHandle *ceInstance)](#oh_contentembed_extension_getextensioninstance) | - | 从ExtensionAbility基类实例中获取对应的OE Extension实例。<br>建议在[OH_AbilityRuntime_OnNativeExtensionCreate](../apis-ability-kit/capi-extension-ability-h.md#oh_abilityruntime_onnativeextensioncreate)函数实现里调用，获取实例后应调用[OH_ContentEmbed_Extension_RegisterOnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeroncreatefunc)和[OH_ContentEmbed_Extension_RegisterOnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondestroyfunc)注册OE Extension生命周期回调函数。 |
| [typedef void (\*OH_ContentEmbed_Extension_OnCreateFunc)(ContentEmbed_ExtensionInstanceHandle instance, AbilityBase_Want *want)](#oh_contentembed_extension_oncreatefunc) | OH_ContentEmbed_Extension_OnCreateFunc | OE Extension实例创建时的生命周期函数类型。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeroncreatefunc)注册到OE Extension实例。 |
| [typedef void (\*OH_ContentEmbed_Extension_OnDestroyFunc)(ContentEmbed_ExtensionInstanceHandle instance)](#oh_contentembed_extension_ondestroyfunc) | OH_ContentEmbed_Extension_OnDestroyFunc | OE Extension实例销毁时的生命周期函数类型。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondestroyfunc)注册到OE Extension实例。 |
| [typedef void (\*OH_ContentEmbed_Extension_OnObjectAttachFunc)(ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_onobjectattachfunc) | OH_ContentEmbed_Extension_OnObjectAttachFunc | 当客户端OE对象连接到OE Extension实例时的回调函数类型，用于执行服务端OE对象关联后的初始化操作。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectattachfunc)注册到OE Extension实例。在此回调中，开发者需要调用[OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronwritetodatastreamfunc)、[OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetcapabilityfunc)、[OH_ContentEmbed_Extension_RegisterOnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondoeditfunc)、[OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetsnapshotfunc)和[OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongeteditstatusfunc)函数注册用于响应客户端OE对象请求的回调函数。 |
| [typedef void (\*OH_ContentEmbed_Extension_OnObjectDetachFunc)(ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_onobjectdetachfunc) | OH_ContentEmbed_Extension_OnObjectDetachFunc | 当客户端OE对象从OE Extension实例断开连接时的回调函数类型，用于执行服务端OE对象断开连接后的清理操作。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectdetachfunc)注册到OE Extension实例。 |
| [typedef void (\*OH_ContentEmbed_Extension_OnWriteToDataStreamFunc)(ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_onwritetodatastreamfunc) | OH_ContentEmbed_Extension_OnWriteToDataStreamFunc | 当服务端OE对象写入OE文档数据流时的回调函数类型。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronwritetodatastreamfunc)注册到服务端OE对象。 |
| [typedef void (\*OH_ContentEmbed_Extension_OnGetSnapshotFunc)(ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_ongetsnapshotfunc) | OH_ContentEmbed_Extension_OnGetSnapshotFunc | 当客户端OE对象请求获取OE文档快照时的回调函数类型。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetsnapshotfunc)注册到服务端OE对象。<br>在此回调中，开发者需要调用[OH_ContentEmbed_Extension_SetSnapshot](capi-content-embed-extension-h.md#oh_contentembed_extension_setsnapshot)设置OE文档快照图像，以响应客户端的快照获取请求。 |
| [typedef void (\*OH_ContentEmbed_Extension_OnDoEditFunc)(ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_ondoeditfunc) | OH_ContentEmbed_Extension_OnDoEditFunc | 当客户端OE对象请求编辑OE文档时的回调函数类型。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondoeditfunc)注册到服务端OE对象。<br>在此回调中，可以通过[OH_ContentEmbed_Extension_ContextStartSelfUIAbility](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiability)和[OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiabilitywithstartoptions)拉起本应用的UIAbility进行编辑。编辑完成后，开发者需要调用[OH_ContentEmbed_Extension_CallbackToOnEditingFinished](capi-content-embed-extension-h.md#oh_contentembed_extension_callbacktooneditingfinished)通知客户端编辑已完成。 |
| [typedef void (\*OH_ContentEmbed_Extension_OnGetEditStatusFunc)(ContentEmbed_ObjectHandle object, bool *isEditing, bool *isModified)](#oh_contentembed_extension_ongeteditstatusfunc) | OH_ContentEmbed_Extension_OnGetEditStatusFunc | 当客户端OE对象请求OE文档编辑状态时的回调函数类型。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongeteditstatusfunc)注册到服务端OE对象。 |
| [typedef void (\*OH_ContentEmbed_Extension_OnGetCapabilityFunc)(ContentEmbed_ObjectHandle object, uint32_t *bitmask)](#oh_contentembed_extension_ongetcapabilityfunc) | OH_ContentEmbed_Extension_OnGetCapabilityFunc | 当客户端OE对象查询OE Extension实例支持能力时的回调函数类型。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetcapabilityfunc)注册到服务端OE对象。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnCreateFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnCreateFunc onCreateFunc)](#oh_contentembed_extension_registeroncreatefunc) | - | 注册OE Extension实例创建时的生命周期函数。<br>该回调注册后不支持取消注册，在实例生命周期内持续有效。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnDestroyFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnDestroyFunc onDestroyFunc)](#oh_contentembed_extension_registerondestroyfunc) | - | 注册OE Extension实例销毁时的生命周期函数。<br>该回调注册后不支持取消注册，在实例生命周期内持续有效。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnObjectAttachFunc onObjectAttachFunc)](#oh_contentembed_extension_registeronobjectattachfunc) | - | 注册客户端OE对象连接时的回调函数。<br>可以通过调用[OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_unregisteronobjectattachfunc)取消注册。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc(ContentEmbed_ExtensionInstanceHandle instance)](#oh_contentembed_extension_unregisteronobjectattachfunc) | - | 取消注册客户端OE对象连接时的回调函数。可以通过调用[OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectattachfunc)重新注册。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnObjectDetachFunc onObjectDetachFunc)](#oh_contentembed_extension_registeronobjectdetachfunc) | - | 注册客户端OE对象断开连接时的回调函数。<br>可以通过调用[OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_unregisteronobjectdetachfunc)取消注册。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc(ContentEmbed_ExtensionInstanceHandle instance)](#oh_contentembed_extension_unregisteronobjectdetachfunc) | - | 取消注册客户端OE对象断开连接时的回调函数。可以通过调用[OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectdetachfunc)重新注册。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnWriteToDataStreamFunc onWriteToDataStreamFunc)](#oh_contentembed_extension_registeronwritetodatastreamfunc) | - | 注册服务端OE对象写入OE文档数据流时的回调函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetSnapshotFunc onGetSnapshotFunc)](#oh_contentembed_extension_registerongetsnapshotfunc) | - | 注册客户端OE对象请求获取OE文档快照时的回调函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnDoEditFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnDoEditFunc onDoEditFunc)](#oh_contentembed_extension_registerondoeditfunc) | - | 注册客户端OE对象请求编辑OE文档时的回调函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetEditStatusFunc onGetEditStatusFunc)](#oh_contentembed_extension_registerongeteditstatusfunc) | - | 注册客户端OE对象请求OE文档编辑状态时的回调函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetCapabilityFunc onGetCapabilityFunc)](#oh_contentembed_extension_registerongetcapabilityfunc) | - | 注册客户端OE对象查询OE Extension实例支持能力时的回调函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContentEmbedDocument(ContentEmbed_ObjectHandle object, ContentEmbed_Document **ceDocument)](#oh_contentembed_extension_getcontentembeddocument) | - | 获取服务端OE对象关联的OE文档实例。文档实例的生命周期由系统管理，无需手动释放。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnUpdate(ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_callbacktoonupdate) | - | 触发客户端OE对象注册的OE文档更新回调函数。<br>当服务端OE文档内容发生变化后调用，通知客户端刷新文档显示。建议在文档数据修改完成后调用，避免在修改过程中频繁触发。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnError(ContentEmbed_ObjectHandle object, ContentEmbed_ErrorCode code)](#oh_contentembed_extension_callbacktoonerror) | - | 触发客户端OE对象注册的OE文档错误回调函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnEditingFinished(ContentEmbed_ObjectHandle object, bool dataModified)](#oh_contentembed_extension_callbacktooneditingfinished) | - | 触发客户端OE对象注册的OE文档编辑完成回调函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnExtensionStopped(ContentEmbed_ExtensionInstanceHandle instance)](#oh_contentembed_extension_callbacktoonextensionstopped) | - | 触发OE Extension关联的所有客户端OE对象注册的OE Extension停止时的回调函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_SetSnapshot(ContentEmbed_ObjectHandle object, OH_PixelmapNative *pixelMap)](#oh_contentembed_extension_setsnapshot) | - | 设置客户端OE对象关联的OE文档快照图像。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextStartSelfUIAbility(ContentEmbed_ExtensionContextHandle context, AbilityBase_Want *want)](#oh_contentembed_extension_contextstartselfuiability) | - | 通过OE Extension上下文启动自身的[UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md#uiability)。如需指定启动选项，参考[OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiabilitywithstartoptions)。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions(ContentEmbed_ExtensionContextHandle context, AbilityBase_Want *want, AbilityRuntime_StartOptions *options)](#oh_contentembed_extension_contextstartselfuiabilitywithstartoptions) | - | 使用启动选项启动OE Extension上下文自身的[UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md#uiability)。如果不需要指定启动选项，参考[OH_ContentEmbed_Extension_ContextStartSelfUIAbility](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiability)。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextTerminateAbility(ContentEmbed_ExtensionContextHandle context)](#oh_contentembed_extension_contextterminateability) | - | 销毁OE Extension。当OE Extension不再需要提供服务时调用，通过上下文销毁Extension实例并释放相关资源。建议在所有客户端OE对象断开连接且完成资源清理后调用，销毁后关联的客户端OE对象将收到Extension停止通知。 |

## 函数说明

### OH_ContentEmbed_Extension_GetContentEmbedContext()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContentEmbedContext(ContentEmbed_ExtensionInstanceHandle ceInstance, ContentEmbed_ExtensionContextHandle *ceContext)
```

**描述**

从OE Extension实例中获取其对应的OE Extension上下文对象。支持通过[OH_ContentEmbed_Extension_GetContext](capi-content-embed-extension-h.md#oh_contentembed_extension_getcontext)获取AbilityRuntime上下文、[OH_ContentEmbed_Extension_ContextStartSelfUIAbility](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiability)或[OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiabilitywithstartoptions)启动自身UIAbility及[OH_ContentEmbed_Extension_ContextTerminateAbility](capi-content-embed-extension-h.md#oh_contentembed_extension_contextterminateability)销毁OE Extension等操作。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) ceInstance | OE Extension实例对象的指针。 |
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) *ceContext | 输出参数。调用成功后，该指针指向OE Extension实例的上下文对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示出现空指针错误。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

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
| [AbilityRuntime_ContextHandle](../apis-ability-kit/capi-abilityruntime-abilityruntime-context8h.md) *context | 输出参数。调用成功后，该指针指向[AbilityRuntime_ContextHandle](../apis-ability-kit/capi-abilityruntime-abilityruntime-context8h.md)上下文对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示出现空指针错误。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_GetExtensionInstance()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetExtensionInstance(AbilityRuntime_ExtensionInstanceHandle baseInstance, ContentEmbed_ExtensionInstanceHandle *ceInstance)
```

**描述**

从ExtensionAbility基类实例中获取对应的OE Extension实例。<br>建议在[OH_AbilityRuntime_OnNativeExtensionCreate](../apis-ability-kit/capi-extension-ability-h.md#oh_abilityruntime_onnativeextensioncreate)函数实现里调用，获取实例后应调用[OH_ContentEmbed_Extension_RegisterOnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeroncreatefunc)和[OH_ContentEmbed_Extension_RegisterOnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondestroyfunc)注册OE Extension生命周期回调函数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [AbilityRuntime_ExtensionInstanceHandle](../apis-ability-kit/capi-abilityruntime-extensioninstance8h.md) baseInstance | 指向[AbilityRuntime_ExtensionInstanceHandle](../apis-ability-kit/capi-abilityruntime-extensioninstance8h.md)基类实例的指针。 |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) *ceInstance | 输出参数。调用成功后，该指针指向OE Extension实例对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示出现空指针错误。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_OnCreateFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnCreateFunc)(ContentEmbed_ExtensionInstanceHandle instance, AbilityBase_Want *want)
```

**描述**

OE Extension实例创建时的生命周期函数类型。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeroncreatefunc)注册到OE Extension实例。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | OE Extension实例对象的指针。 |
| [AbilityBase_Want](../apis-ability-kit/capi-abilitybase-want.md) \*want | 指向[AbilityBase_Want](../apis-ability-kit/capi-abilitybase-want.md)实例的指针，包含OE Extension创建时传递的启动参数。 |

### OH_ContentEmbed_Extension_OnDestroyFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnDestroyFunc)(ContentEmbed_ExtensionInstanceHandle instance)
```

**描述**

OE Extension实例销毁时的生命周期函数类型。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondestroyfunc)注册到OE Extension实例。

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

当客户端OE对象连接到OE Extension实例时的回调函数类型，用于执行服务端OE对象关联后的初始化操作。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectattachfunc)注册到OE Extension实例。在此回调中，开发者需要调用[OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronwritetodatastreamfunc)、[OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetcapabilityfunc)、[OH_ContentEmbed_Extension_RegisterOnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondoeditfunc)、[OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetsnapshotfunc)和[OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongeteditstatusfunc)函数注册用于响应客户端OE对象请求的回调函数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | OE Extension实例对象的指针。 |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md)实例。 |

### OH_ContentEmbed_Extension_OnObjectDetachFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnObjectDetachFunc)(ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object)
```

**描述**

当客户端OE对象从OE Extension实例断开连接时的回调函数类型，用于执行服务端OE对象断开连接后的清理操作。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectdetachfunc)注册到OE Extension实例。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | OE Extension实例对象的指针。 |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md)实例。 |

### OH_ContentEmbed_Extension_OnWriteToDataStreamFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnWriteToDataStreamFunc)(ContentEmbed_ObjectHandle object)
```

**描述**

当服务端OE对象写入OE文档数据流时的回调函数类型。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronwritetodatastreamfunc)注册到服务端OE对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md)实例。 |

### OH_ContentEmbed_Extension_OnGetSnapshotFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnGetSnapshotFunc)(ContentEmbed_ObjectHandle object)
```

**描述**

当客户端OE对象请求获取OE文档快照时的回调函数类型。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetsnapshotfunc)注册到服务端OE对象。<br>在此回调中，开发者需要调用[OH_ContentEmbed_Extension_SetSnapshot](capi-content-embed-extension-h.md#oh_contentembed_extension_setsnapshot)设置OE文档快照图像，以响应客户端的快照获取请求。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md)实例。 |

### OH_ContentEmbed_Extension_OnDoEditFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnDoEditFunc)(ContentEmbed_ObjectHandle object)
```

**描述**

当客户端OE对象请求编辑OE文档时的回调函数类型。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondoeditfunc)注册到服务端OE对象。<br>在此回调中，可以通过[OH_ContentEmbed_Extension_ContextStartSelfUIAbility](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiability)和[OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiabilitywithstartoptions)拉起本应用的UIAbility进行编辑。编辑完成后，开发者需要调用[OH_ContentEmbed_Extension_CallbackToOnEditingFinished](capi-content-embed-extension-h.md#oh_contentembed_extension_callbacktooneditingfinished)通知客户端编辑已完成。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md)实例。 |

### OH_ContentEmbed_Extension_OnGetEditStatusFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnGetEditStatusFunc)(ContentEmbed_ObjectHandle object, bool *isEditing, bool *isModified)
```

**描述**

当客户端OE对象请求OE文档编辑状态时的回调函数类型。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongeteditstatusfunc)注册到服务端OE对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md)实例。 |
| bool \*isEditing | 输出参数。表示OE文档是否正在编辑，true表示正在编辑；false表示未编辑。 |
| bool \*isModified | 输出参数。表示OE文档是否已被修改，true表示已被修改；false表示未修改。 |

### OH_ContentEmbed_Extension_OnGetCapabilityFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnGetCapabilityFunc)(ContentEmbed_ObjectHandle object, uint32_t *bitmask)
```

**描述**

当客户端OE对象查询OE Extension实例支持能力时的回调函数类型。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetcapabilityfunc)注册到服务端OE对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md)实例。 |
| uint32_t \*bitmask | 输出参数，表示OE Extension实例支持的能力，由[ContentEmbed_CapabilityCode](capi-content-embed-common-h.md#contentembed_capabilitycode)中的值组合而成。 |

### OH_ContentEmbed_Extension_RegisterOnCreateFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnCreateFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnCreateFunc onCreateFunc)
```

**描述**

注册OE Extension实例创建时的生命周期函数。<br>该回调注册后不支持取消注册，在实例生命周期内持续有效。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | 指向OE Extension实例对象的指针。 |
| [OH_ContentEmbed_Extension_OnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_oncreatefunc) onCreateFunc | 要注册的[OH_ContentEmbed_Extension_OnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_oncreatefunc)生命周期函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_RegisterOnDestroyFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnDestroyFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnDestroyFunc onDestroyFunc)
```

**描述**

注册OE Extension实例销毁时的生命周期函数。<br>该回调注册后不支持取消注册，在实例生命周期内持续有效。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | 指向OE Extension实例对象的指针。 |
| [OH_ContentEmbed_Extension_OnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ondestroyfunc) onDestroyFunc | 要注册的[OH_ContentEmbed_Extension_OnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ondestroyfunc)生命周期函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnObjectAttachFunc onObjectAttachFunc)
```

**描述**

注册客户端OE对象连接时的回调函数。<br>可以通过调用[OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_unregisteronobjectattachfunc)取消注册。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | 指向OE Extension实例对象的指针。 |
| [OH_ContentEmbed_Extension_OnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onobjectattachfunc) onObjectAttachFunc | 要注册的[OH_ContentEmbed_Extension_OnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onobjectattachfunc)回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc(ContentEmbed_ExtensionInstanceHandle instance)
```

**描述**

取消注册客户端OE对象连接时的回调函数。可以通过调用[OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectattachfunc)重新注册。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | 指向OE Extension实例对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnObjectDetachFunc onObjectDetachFunc)
```

**描述**

注册客户端OE对象断开连接时的回调函数。<br>可以通过调用[OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_unregisteronobjectdetachfunc)取消注册。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | 指向OE Extension实例对象的指针。 |
| [OH_ContentEmbed_Extension_OnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onobjectdetachfunc) onObjectDetachFunc | 要注册的[OH_ContentEmbed_Extension_OnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onobjectdetachfunc)回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc(ContentEmbed_ExtensionInstanceHandle instance)
```

**描述**

取消注册客户端OE对象断开连接时的回调函数。可以通过调用[OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectdetachfunc)重新注册。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | 指向OE Extension实例对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

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
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md)实例。 |
| [OH_ContentEmbed_Extension_OnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onwritetodatastreamfunc) onWriteToDataStreamFunc | 要注册的[OH_ContentEmbed_Extension_OnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onwritetodatastreamfunc)回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

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
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md)实例。 |
| [OH_ContentEmbed_Extension_OnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongetsnapshotfunc) onGetSnapshotFunc | 要注册的[OH_ContentEmbed_Extension_OnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongetsnapshotfunc)回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

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
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md)实例。 |
| [OH_ContentEmbed_Extension_OnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ondoeditfunc) onDoEditFunc | 要注册的[OH_ContentEmbed_Extension_OnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ondoeditfunc)回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetEditStatusFunc onGetEditStatusFunc)
```

**描述**

注册客户端OE对象请求OE文档编辑状态时的回调函数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md)实例。 |
| [OH_ContentEmbed_Extension_OnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongeteditstatusfunc) onGetEditStatusFunc | 要注册的[OH_ContentEmbed_Extension_OnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongeteditstatusfunc)回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetCapabilityFunc onGetCapabilityFunc)
```

**描述**

注册客户端OE对象查询OE Extension实例支持能力时的回调函数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md)实例。 |
| [OH_ContentEmbed_Extension_OnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongetcapabilityfunc) onGetCapabilityFunc | 要注册的[OH_ContentEmbed_Extension_OnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongetcapabilityfunc)回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_GetContentEmbedDocument()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContentEmbedDocument(ContentEmbed_ObjectHandle object, ContentEmbed_Document **ceDocument)
```

**描述**

获取服务端OE对象关联的OE文档实例。文档实例的生命周期由系统管理，无需手动释放。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md)实例。 |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) **ceDocument | 输出参数。调用成功后，该指针指向关联的OE文档实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示出现空指针错误。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_CallbackToOnUpdate()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnUpdate(ContentEmbed_ObjectHandle object)
```

**描述**

触发客户端OE对象注册的OE文档更新回调函数。<br>当服务端OE文档内容发生变化后调用，通知客户端刷新文档显示。建议在文档数据修改完成后调用，避免在修改过程中频繁触发。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md)实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示出现空指针错误。<br>     CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED：表示客户端回调未注册。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_CLIENT_CALLBACK_FAILED：表示客户端回调执行失败。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

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
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md)实例。 |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) code | 表示错误码，详细定义参见[ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示出现空指针错误。<br>     CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED：表示客户端回调未注册。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_CLIENT_CALLBACK_FAILED：表示客户端回调执行失败。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

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
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md)实例。 |
| bool dataModified | 表示文档数据是否已被修改。true表示有修改，false表示无修改。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示出现空指针错误。<br>     CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED：表示客户端回调未注册。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_CLIENT_CALLBACK_FAILED：表示客户端回调执行失败。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_CallbackToOnExtensionStopped()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnExtensionStopped(ContentEmbed_ExtensionInstanceHandle instance)
```

**描述**

触发OE Extension关联的所有客户端OE对象注册的OE Extension停止时的回调函数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | 指向OE Extension实例对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示出现空指针错误。<br>     CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED：表示客户端回调未注册。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_CLIENT_CALLBACK_FAILED：表示客户端回调执行失败。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

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
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md)实例。 |
| [OH_PixelmapNative](../apis-arkgraphics2d/capi-drawing-oh-pixelmapnative.md) *pixelMap | 文档快照的像素图对象，详细信息参考[OH_PixelmapNative](../apis-arkgraphics2d/capi-drawing-oh-pixelmapnative.md)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示出现空指针错误。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。<br>     CE_ERR_IMAGE_PACKER_OPERATION_FAILED：表示ImagePacker操作失败。 |

### OH_ContentEmbed_Extension_ContextStartSelfUIAbility()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextStartSelfUIAbility(ContentEmbed_ExtensionContextHandle context, AbilityBase_Want *want)
```

**描述**

通过OE Extension上下文启动自身的[UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md#uiability)。如需指定启动选项，参考[OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiabilitywithstartoptions)。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) context | 指向OE Extension上下文对象的指针。 |
| [AbilityBase_Want](../apis-ability-kit/capi-abilitybase-want.md) *want | 启动UIAbility时传递的参数，详细信息参考[AbilityBase_Want](../apis-ability-kit/capi-abilitybase-want.md)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示出现空指针错误。<br>     CE_ERR_SYSTEM_ABNORMAL：表示系统服务异常。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions(ContentEmbed_ExtensionContextHandle context, AbilityBase_Want *want, AbilityRuntime_StartOptions *options)
```

**描述**

使用启动选项启动OE Extension上下文自身的[UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md#uiability)。如果不需要指定启动选项，参考[OH_ContentEmbed_Extension_ContextStartSelfUIAbility](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiability)。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) context | 指向OE Extension上下文对象的指针。 |
| [AbilityBase_Want](../apis-ability-kit/capi-abilitybase-want.md) *want | 启动UIAbility时传递的参数，详细信息参考[AbilityBase_Want](../apis-ability-kit/capi-abilitybase-want.md)。 |
| [AbilityRuntime_StartOptions](../apis-ability-kit/capi-abilityruntime-startoptions.md) *options | 启动UIAbility时的附加选项，详细信息参考[AbilityRuntime_StartOptions](../apis-ability-kit/capi-abilityruntime-startoptions.md)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示出现空指针错误。<br>     CE_ERR_SYSTEM_ABNORMAL：表示系统服务异常。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Extension_ContextTerminateAbility()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextTerminateAbility(ContentEmbed_ExtensionContextHandle context)
```

**描述**

销毁OE Extension。当OE Extension不再需要提供服务时调用，通过上下文销毁Extension实例并释放相关资源。建议在所有客户端OE对象断开连接且完成资源清理后调用，销毁后关联的客户端OE对象将收到Extension停止通知。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) context | 指向OE Extension上下文对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示出现空指针错误。<br>     CE_ERR_SYSTEM_ABNORMAL：表示系统服务异常。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |


