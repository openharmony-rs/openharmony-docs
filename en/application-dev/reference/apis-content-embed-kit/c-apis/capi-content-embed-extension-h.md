# content_embed_extension.h

## Overview

Defines the data structures and operation APIs related to the OE Extension of the server application.

**Library**: libcontent_embed_ndk.so

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Related module**: [ContentEmbed](capi-contentembed.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) | ContentEmbed_Document | Declares the structure type of an OE document. Encapsulates the metadata, content, and storage structure of the embedded document. |
| [ContentEmbed_ExtensionContext](capi-contentembed-contentembed-extensioncontext.md) | ContentEmbed_ExtensionContext | Defines the structure type of the OE Extension context. |
| [ContentEmbed_ExtensionContext*](capi-contentembed-contentembed-extensioncontext8h.md) | ContentEmbed_ExtensionContextHandle | Declares the pointer type of the context object of the OE Extension. |
| [ContentEmbed_ExtensionInstance](capi-contentembed-contentembed-extensioninstance.md) | ContentEmbed_ExtensionInstance | Declares the structure type of an OE Extension instance. Manages the core functions of the extension, such as lifecycle management, callback registration, and association with the client's OE object. |
| [ContentEmbed_ExtensionInstance*](capi-contentembed-contentembed-extensioninstance8h.md) | ContentEmbed_ExtensionInstanceHandle | Declares the pointer type of the instance object of the ContentEmbed extension. |
| [ContentEmbed_Object](capi-contentembed-contentembed-object.md) | ContentEmbed_Object | Declares the ContentEmbed_Object structure. Points to the program object (server-side OE object for short) for embedding and editing the OE document encapsulated by the server. |
| [ContentEmbed_Object*](capi-contentembed-contentembed-object8h.md) | ContentEmbed_ObjectHandle | Declares the pointer type of the ContentEmbed_Object object. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContentEmbedContext(ContentEmbed_ExtensionInstanceHandle ceInstance, ContentEmbed_ExtensionContextHandle *ceContext)](#oh_contentembed_extension_getcontentembedcontext) | - | Obtains the corresponding OE Extension context object from the OE Extension instance. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContext(ContentEmbed_ExtensionContextHandle ceContext, AbilityRuntime_ContextHandle *context)](#oh_contentembed_extension_getcontext) | - | Obtains the AbilityRuntime context from the OE Extension context. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetExtensionInstance(AbilityRuntime_ExtensionInstanceHandle baseInstance, ContentEmbed_ExtensionInstanceHandle *ceInstance)](#oh_contentembed_extension_getextensioninstance) | - | Obtains the corresponding OE Extension instance from the ExtensionAbility base class instance. |
| [typedef void (\*OH_ContentEmbed_Extension_OnCreateFunc)(ContentEmbed_ExtensionInstanceHandle instance, AbilityBase_Want *want)](#oh_contentembed_extension_oncreatefunc) | OH_ContentEmbed_Extension_OnCreateFunc | Indicates the lifecycle function type when an OE Extension instance is created. <br>You need to implement this function and register it with the OE Extension instance through [OH_ContentEmbed_Extension_RegisterOnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeroncreatefunc). |
| [typedef void (\*OH_ContentEmbed_Extension_OnDestroyFunc)(ContentEmbed_ExtensionInstanceHandle instance)](#oh_contentembed_extension_ondestroyfunc) | OH_ContentEmbed_Extension_OnDestroyFunc | Indicates the lifecycle function type when an OE Extension instance is destroyed. <br>You need to implement this function and register it with the OE Extension instance through [OH_ContentEmbed_Extension_RegisterOnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondestroyfunc). |
| [typedef void (\*OH_ContentEmbed_Extension_OnObjectAttachFunc)(ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_onobjectattachfunc) | OH_ContentEmbed_Extension_OnObjectAttachFunc | This callback function is triggered when the client's OE object is connected to the OE Extension instance. It is used to perform the initialization operation after the server's OE object is associated. <br>You need to implement this function and register it with the OE Extension instance through [OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectattachfunc). |
| [typedef void (\*OH_ContentEmbed_Extension_OnObjectDetachFunc)(ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_onobjectdetachfunc) | OH_ContentEmbed_Extension_OnObjectDetachFunc | This callback function is triggered when the client disconnects from the OE Extension instance, and is used to perform cleanup operations after the server disconnects from the OE Extension instance. <br>You need to implement this function and register it with the OE Extension instance through [OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectdetachfunc). |
| [typedef void (\*OH_ContentEmbed_Extension_OnWriteToDataStreamFunc)(ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_onwritetodatastreamfunc) | OH_ContentEmbed_Extension_OnWriteToDataStreamFunc | Callback function type used when the server-side OE object writes data to the OE document. <br>You need to implement this function and register it with the server-side OE object through [OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronwritetodatastreamfunc). |
| [typedef void (\*OH_ContentEmbed_Extension_OnGetSnapshotFunc)(ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_ongetsnapshotfunc) | OH_ContentEmbed_Extension_OnGetSnapshotFunc | Callback function type used when the client-side OE object requests to obtain the OE document snapshot. <br>You need to implement this function and register it with the server-side OE object through [OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetsnapshotfunc). |
| [typedef void (\*OH_ContentEmbed_Extension_OnDoEditFunc)(ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_ondoeditfunc) | OH_ContentEmbed_Extension_OnDoEditFunc | Callback function type when the client's OE object requests to edit an OE document. <br>You need to implement this function and register it with the server's OE object through [OH_ContentEmbed_Extension_RegisterOnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondoeditfunc). |
| [typedef void (\*OH_ContentEmbed_Extension_OnGetEditStatusFunc)(ContentEmbed_ObjectHandle object, bool *isEditing, bool *isModified)](#oh_contentembed_extension_ongeteditstatusfunc) | OH_ContentEmbed_Extension_OnGetEditStatusFunc | Callback function type when the client's OE object requests the editing state of an OE document. <br>You need to implement this function and register it with the server's OE object through [OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongeteditstatusfunc). |
| [typedef void (\*OH_ContentEmbed_Extension_OnGetCapabilityFunc)(ContentEmbed_ObjectHandle object, uint32_t *bitmask)](#oh_contentembed_extension_ongetcapabilityfunc) | OH_ContentEmbed_Extension_OnGetCapabilityFunc | Indicates the callback function type when the client queries the capabilities supported by the OE Extension instance. <br>You need to implement this function and register it with the server-side OE object through [OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetcapabilityfunc). |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnCreateFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnCreateFunc onCreateFunc)](#oh_contentembed_extension_registeroncreatefunc) | - | Registers the lifecycle function for creating an OE Extension instance. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnDestroyFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnDestroyFunc onDestroyFunc)](#oh_contentembed_extension_registerondestroyfunc) | - | Registers the lifecycle function for destroying an OE Extension instance. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnObjectAttachFunc onObjectAttachFunc)](#oh_contentembed_extension_registeronobjectattachfunc) | - | Registers the callback function for connecting to the client's OE object. <br>You can call [OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_unregisteronobjectattachfunc) to deregister the callback function. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc(ContentEmbed_ExtensionInstanceHandle instance)](#oh_contentembed_extension_unregisteronobjectattachfunc) | - | Cancels the registration of the callback function for disconnecting the client from the OE object. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnObjectDetachFunc onObjectDetachFunc)](#oh_contentembed_extension_registeronobjectdetachfunc) | - | Registers the callback function for disconnecting the client from the OE object. <br>You can call [OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_unregisteronobjectdetachfunc) to cancel the registration. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc(ContentEmbed_ExtensionInstanceHandle instance)](#oh_contentembed_extension_unregisteronobjectdetachfunc) | - | Cancels the callback function for disconnecting the client from the OE object. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnWriteToDataStreamFunc onWriteToDataStreamFunc)](#oh_contentembed_extension_registeronwritetodatastreamfunc) | - | Registers the callback function for the server to write data streams to the OE document. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetSnapshotFunc onGetSnapshotFunc)](#oh_contentembed_extension_registerongetsnapshotfunc) | - | Registers the callback function for obtaining the OE document snapshot when the client requests to obtain the OE document snapshot. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnDoEditFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnDoEditFunc onDoEditFunc)](#oh_contentembed_extension_registerondoeditfunc) | - | Registers the callback function for editing an OE document when the client requests to edit the OE document. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetEditStatusFunc onGetEditStatusFunc)](#oh_contentembed_extension_registerongeteditstatusfunc) | - | Registers the callback function for requesting the editing state of an OE document from the client. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetCapabilityFunc onGetCapabilityFunc)](#oh_contentembed_extension_registerongetcapabilityfunc) | - | Registers the callback function for querying whether the OE Extension instance supports the capability of the client's OE object. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContentEmbedDocument(ContentEmbed_ObjectHandle object, ContentEmbed_Document **ceDocument)](#oh_contentembed_extension_getcontentembeddocument) | - | Obtains the instance of the OE document associated with the server-side OE object. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnUpdate(ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_callbacktoonupdate) | - | Triggers the callback function for updating the OE document to register the client's OE object. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnError(ContentEmbed_ObjectHandle object, ContentEmbed_ErrorCode code)](#oh_contentembed_extension_callbacktoonerror) | - | Trigger the callback function of the error in the OE document that triggers the registration of the client's OE object. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnEditingFinished(ContentEmbed_ObjectHandle object, bool dataModified)](#oh_contentembed_extension_callbacktooneditingfinished) | - | Registers the callback function for finishing editing an OE document. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnExtensionStopped(ContentEmbed_ExtensionInstanceHandle instance)](#oh_contentembed_extension_callbacktoonextensionstopped) | - | Stops the callback function of the OE Extension that is associated with all client-side OE objects and registered by the OE Extension. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_SetSnapshot(ContentEmbed_ObjectHandle object, OH_PixelmapNative *pixelMap)](#oh_contentembed_extension_setsnapshot) | - | Sets the snapshot image of the OE document associated with the client-side OE object. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextStartSelfUIAbility(ContentEmbed_ExtensionContextHandle context, AbilityBase_Want *want)](#oh_contentembed_extension_contextstartselfuiability) | - | Starts the {@link UIAbility} of the current instance using the OE Extension context. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions(ContentEmbed_ExtensionContextHandle context, AbilityBase_Want *want, AbilityRuntime_StartOptions *options)](#oh_contentembed_extension_contextstartselfuiabilitywithstartoptions) | - | Starts the {@link UIAbility} of the OE Extension context using the start options. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextTerminateAbility(ContentEmbed_ExtensionContextHandle context)](#oh_contentembed_extension_contextterminateability) | - | Destroys the OE Extension. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_ContentEmbed_Extension_OnCreateFunc)( ContentEmbed_ExtensionInstanceHandle instance, AbilityBase_Want *want) | Indicates the lifecycle function type when an OE Extension instance is created. <br>You need to implement this function and register it with the OE Extension instance through [OH_ContentEmbed_Extension_RegisterOnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeroncreatefunc).<br>**Since**: 24 |
| void (*OH_ContentEmbed_Extension_OnDestroyFunc)( ContentEmbed_ExtensionInstanceHandle instance) | Indicates the lifecycle function type when an OE Extension instance is destroyed. <br>You need to implement this function and register it with the OE Extension instance through [OH_ContentEmbed_Extension_RegisterOnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondestroyfunc).<br>**Since**: 24 |
| void (*OH_ContentEmbed_Extension_OnObjectAttachFunc)( ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object) | This callback function is triggered when the client's OE object is connected to the OE Extension instance. It is used to perform the initialization operation after the server's OE object is associated. <br>You need to implement this function and register it with the OE Extension instance through [OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectattachfunc).<br>**Since**: 24 |
| void (*OH_ContentEmbed_Extension_OnObjectDetachFunc)( ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object) | This callback function is triggered when the client disconnects from the OE Extension instance, and is used to perform cleanup operations after the server disconnects from the OE Extension instance. <br>You need to implement this function and register it with the OE Extension instance through [OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectdetachfunc).<br>**Since**: 24 |
| void (*OH_ContentEmbed_Extension_OnWriteToDataStreamFunc)( ContentEmbed_ObjectHandle object) | Callback function type used when the server-side OE object writes data to the OE document. <br>You need to implement this function and register it with the server-side OE object through [OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronwritetodatastreamfunc).<br>**Since**: 24 |
| void (*OH_ContentEmbed_Extension_OnGetSnapshotFunc)( ContentEmbed_ObjectHandle object) | Callback function type used when the client-side OE object requests to obtain the OE document snapshot. <br>You need to implement this function and register it with the server-side OE object through [OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetsnapshotfunc).<br>**Since**: 24 |
| void (*OH_ContentEmbed_Extension_OnDoEditFunc)( ContentEmbed_ObjectHandle object) | Callback function type when the client's OE object requests to edit an OE document. <br>You need to implement this function and register it with the server's OE object through [OH_ContentEmbed_Extension_RegisterOnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondoeditfunc).<br>**Since**: 24 |
| void (*OH_ContentEmbed_Extension_OnGetEditStatusFunc)( ContentEmbed_ObjectHandle object, bool *isEditing, bool *isModified) | Callback function type when the client's OE object requests the editing state of an OE document. <br>You need to implement this function and register it with the server's OE object through [OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongeteditstatusfunc).<br>**Since**: 24 |
| void (*OH_ContentEmbed_Extension_OnGetCapabilityFunc)( ContentEmbed_ObjectHandle object, uint32_t *bitmask) | Indicates the callback function type when the client queries the capabilities supported by the OE Extension instance. <br>You need to implement this function and register it with the server-side OE object through [OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetcapabilityfunc).<br>**Since**: 24 |

## Function description

### OH_ContentEmbed_Extension_GetContentEmbedContext()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContentEmbedContext(ContentEmbed_ExtensionInstanceHandle ceInstance, ContentEmbed_ExtensionContextHandle *ceContext)
```

**Description**

Obtains the corresponding OE Extension context object from the OE Extension instance.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) ceInstance | Pointer to the OE Extension instance object. |
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) *ceContext | Output parameter. After the function is successfully called, this pointer points to the context object of the OE Extension instance. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - indicates that the operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Parameter check failed.</li>      <li>[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode) - A null pointer is returned.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is not supported because the application is in the DLP sandbox.      </li>          </ul> |

### OH_ContentEmbed_Extension_GetContext()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContext(ContentEmbed_ExtensionContextHandle ceContext, AbilityRuntime_ContextHandle *context)
```

**Description**

Obtains the AbilityRuntime context from the OE Extension context.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) ceContext | Pointer to the OE Extension context object. |
| AbilityRuntime_ContextHandle *context | Output parameter. After the call is successful, this pointer points to the {@link AbilityRuntime_Context} context object. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Parameter check failed.</li>      <li>[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode) - A null pointer is returned.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is not supported because the application is in the DLP sandbox.      </li>          </ul> |

### OH_ContentEmbed_Extension_GetExtensionInstance()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetExtensionInstance(AbilityRuntime_ExtensionInstanceHandle baseInstance, ContentEmbed_ExtensionInstanceHandle *ceInstance)
```

**Description**

Obtains the corresponding OE Extension instance from the ExtensionAbility base class instance.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_ExtensionInstanceHandle baseInstance | {@link AbilityRuntime_ExtensionInstance} instance. |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) *ceInstance | Output parameter. After the call is successful, this pointer points to the OE Extension instance object. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Failed to check the parameter.</li>      <li>[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode) - A null pointer is returned.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is not supported because the application is in the DLP sandbox.      </li>          </ul> |

### OH_ContentEmbed_Extension_OnCreateFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnCreateFunc)(ContentEmbed_ExtensionInstanceHandle instance, AbilityBase_Want *want)
```

**Description**

Indicates the lifecycle function type when an OE Extension instance is created. <br>You need to implement this function and register it with the OE Extension instance through [OH_ContentEmbed_Extension_RegisterOnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeroncreatefunc).

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance object. |
| AbilityBase_Want \*want | Represents a pointer to an {@link AbilityBase_Want} instance. |

### OH_ContentEmbed_Extension_OnDestroyFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnDestroyFunc)(ContentEmbed_ExtensionInstanceHandle instance)
```

**Description**

Indicates the lifecycle function type when an OE Extension instance is destroyed. <br>You need to implement this function and register it with the OE Extension instance through [OH_ContentEmbed_Extension_RegisterOnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondestroyfunc).

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance object. |

### OH_ContentEmbed_Extension_OnObjectAttachFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnObjectAttachFunc)(ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object)
```

**Description**

This callback function is triggered when the client's OE object is connected to the OE Extension instance. It is used to perform the initialization operation after the server's OE object is associated. <br>You need to implement this function and register it with the OE Extension instance through [OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectattachfunc).

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance object. |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance. |

### OH_ContentEmbed_Extension_OnObjectDetachFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnObjectDetachFunc)(ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object)
```

**Description**

This callback function is triggered when the client disconnects from the OE Extension instance, and is used to perform cleanup operations after the server disconnects from the OE Extension instance. <br>You need to implement this function and register it with the OE Extension instance through [OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectdetachfunc).

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance object. |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance. |

### OH_ContentEmbed_Extension_OnWriteToDataStreamFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnWriteToDataStreamFunc)(ContentEmbed_ObjectHandle object)
```

**Description**

Callback function type used when the server-side OE object writes data to the OE document. <br>You need to implement this function and register it with the server-side OE object through [OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronwritetodatastreamfunc).

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance. |

### OH_ContentEmbed_Extension_OnGetSnapshotFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnGetSnapshotFunc)(ContentEmbed_ObjectHandle object)
```

**Description**

Callback function type used when the client-side OE object requests to obtain the OE document snapshot. <br>You need to implement this function and register it with the server-side OE object through [OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetsnapshotfunc).

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance. |

### OH_ContentEmbed_Extension_OnDoEditFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnDoEditFunc)(ContentEmbed_ObjectHandle object)
```

**Description**

Callback function type when the client's OE object requests to edit an OE document. <br>You need to implement this function and register it with the server's OE object through [OH_ContentEmbed_Extension_RegisterOnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondoeditfunc).

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance. |

### OH_ContentEmbed_Extension_OnGetEditStatusFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnGetEditStatusFunc)(ContentEmbed_ObjectHandle object, bool *isEditing, bool *isModified)
```

**Description**

Callback function type when the client's OE object requests the editing state of an OE document. <br>You need to implement this function and register it with the server's OE object through [OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongeteditstatusfunc).

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance. |
| bool \*isEditing | Indicates that the content embed document is being edited. |
| bool \*isModified | Indicates that the content embed document has been modified. |

### OH_ContentEmbed_Extension_OnGetCapabilityFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnGetCapabilityFunc)(ContentEmbed_ObjectHandle object, uint32_t *bitmask)
```

**Description**

Indicates the callback function type when the client queries the capabilities supported by the OE Extension instance. <br>You need to implement this function and register it with the server-side OE object through [OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetcapabilityfunc).

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance. |
| uint32_t \*bitmask | Indicates the capabilities possessed by a content embed extension instance. |

### OH_ContentEmbed_Extension_RegisterOnCreateFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnCreateFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnCreateFunc onCreateFunc)
```

**Description**

Registers the lifecycle function for creating an OE Extension instance.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance object. |
| [OH_ContentEmbed_Extension_OnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_oncreatefunc) onCreateFunc | [OH_ContentEmbed_Extension_OnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_oncreatefunc) lifecycle function to be registered. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - The parameter check fails.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - This operation is not supported because the application is in      the DLP sandbox.</li>          </ul> |

### OH_ContentEmbed_Extension_RegisterOnDestroyFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnDestroyFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnDestroyFunc onDestroyFunc)
```

**Description**

Registers the lifecycle function for destroying an OE Extension instance.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance object. |
| [OH_ContentEmbed_Extension_OnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ondestroyfunc) onDestroyFunc | [OH_ContentEmbed_Extension_OnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ondestroyfunc) lifecycle function to be registered. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - The parameter check fails.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - This operation is not supported because the application is in      the DLP sandbox.</li>          </ul> |

### OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnObjectAttachFunc onObjectAttachFunc)
```

**Description**

Registers the callback function for connecting to the client's OE object. <br>You can call [OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_unregisteronobjectattachfunc) to deregister the callback function.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance object. |
| [OH_ContentEmbed_Extension_OnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onobjectattachfunc) onObjectAttachFunc | [OH_ContentEmbed_Extension_OnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onobjectattachfunc) callback function to be registered. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - The parameter check fails.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is not supported because the application is in the DLP sandbox.      </li>          </ul> |

### OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc(ContentEmbed_ExtensionInstanceHandle instance)
```

**Description**

Cancels the registration of the callback function for disconnecting the client from the OE object.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance object. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Failed to check the parameter.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is not supported because the application is in the DLP sandbox.      </li>          </ul> |

### OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnObjectDetachFunc onObjectDetachFunc)
```

**Description**

Registers the callback function for disconnecting the client from the OE object. <br>You can call [OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_unregisteronobjectdetachfunc) to cancel the registration.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the instance object of the OE Extension. |
| [OH_ContentEmbed_Extension_OnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onobjectdetachfunc) onObjectDetachFunc | [OH_ContentEmbed_Extension_OnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onobjectdetachfunc) callback function to be registered. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Failed to check the parameter.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - This operation is not supported because the application is in      the DLP sandbox.</li>          </ul> |

### OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc(ContentEmbed_ExtensionInstanceHandle instance)
```

**Description**

Cancels the callback function for disconnecting the client from the OE object.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance object. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - The parameter check fails.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - This operation is not supported because the application is in      the DLP sandbox.</li>          </ul> |

### OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnWriteToDataStreamFunc onWriteToDataStreamFunc)
```

**Description**

Registers the callback function for the server to write data streams to the OE document.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance. |
| [OH_ContentEmbed_Extension_OnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onwritetodatastreamfunc) onWriteToDataStreamFunc | [OH_ContentEmbed_Extension_OnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onwritetodatastreamfunc) callback function to be registered. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Failed to check the parameter.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - This operation is not supported because the application is in      the DLP sandbox.</li>          </ul> |

### OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetSnapshotFunc onGetSnapshotFunc)
```

**Description**

Registers the callback function for obtaining the OE document snapshot when the client requests to obtain the OE document snapshot.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance. |
| [OH_ContentEmbed_Extension_OnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongetsnapshotfunc) onGetSnapshotFunc | [OH_ContentEmbed_Extension_OnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongetsnapshotfunc) callback function to be registered. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Failed to check the parameter.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - This operation is not supported because the application is in      the DLP sandbox.</li>          </ul> |

### OH_ContentEmbed_Extension_RegisterOnDoEditFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnDoEditFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnDoEditFunc onDoEditFunc)
```

**Description**

Registers the callback function for editing an OE document when the client requests to edit the OE document.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance. |
| [OH_ContentEmbed_Extension_OnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ondoeditfunc) onDoEditFunc | [OH_ContentEmbed_Extension_OnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ondoeditfunc) callback function to be registered. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Failed to check the parameter.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - This operation is not supported because the application is in      the DLP sandbox.</li>          </ul> |

### OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetEditStatusFunc onGetEditStatusFunc)
```

**Description**

Registers the callback function for requesting the editing state of an OE document from the client.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance. |
| [OH_ContentEmbed_Extension_OnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongeteditstatusfunc) onGetEditStatusFunc | [OH_ContentEmbed_Extension_OnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongeteditstatusfunc) callback function to be registered. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Failed to check the parameter.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - This operation is not supported because the application is in      the DLP sandbox.</li>          </ul> |

### OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetCapabilityFunc onGetCapabilityFunc)
```

**Description**

Registers the callback function for querying whether the OE Extension instance supports the capability of the client's OE object.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance. |
| [OH_ContentEmbed_Extension_OnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongetcapabilityfunc) onGetCapabilityFunc | [OH_ContentEmbed_Extension_OnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongetcapabilityfunc) callback function to be registered. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Failed to check the parameter.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - This operation is not supported because the application is in      the DLP sandbox.</li>          </ul> |

### OH_ContentEmbed_Extension_GetContentEmbedDocument()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContentEmbedDocument(ContentEmbed_ObjectHandle object, ContentEmbed_Document **ceDocument)
```

**Description**

Obtains the instance of the OE document associated with the server-side OE object.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance. |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) **ceDocument | Output parameter. After the call is successful, this pointer points to the associated OE document instance. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - The parameter check fails.</li>      <li>[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode) - A null pointer is returned.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is not supported because the application is in the DLP sandbox.      </li>          </ul> |

### OH_ContentEmbed_Extension_CallbackToOnUpdate()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnUpdate(ContentEmbed_ObjectHandle object)
```

**Description**

Triggers the callback function for updating the OE document to register the client's OE object.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - The parameter check fails.</li>      <li>[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode) - A null pointer is returned.</li>      <li>[CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED](capi-content-embed-common-h.md#contentembed_errorcode) - The client callback is not registered.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_CLIENT_CALLBACK_FAILED](capi-content-embed-common-h.md#contentembed_errorcode) - The client callback fails to be executed.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - This operation is not supported because the application is in      the DLP sandbox.</li>          </ul> |

### OH_ContentEmbed_Extension_CallbackToOnError()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnError(ContentEmbed_ObjectHandle object, ContentEmbed_ErrorCode code)
```

**Description**

Trigger the callback function of the error in the OE document that triggers the registration of the client's OE object.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance. |
| ContentEmbed_ErrorCode code | Error code. For details, see [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode). |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - The parameter check fails.</li>      <li>[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode) - A null pointer is returned.</li>      <li>[CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED](capi-content-embed-common-h.md#contentembed_errorcode) - The client callback is not registered.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_CLIENT_CALLBACK_FAILED](capi-content-embed-common-h.md#contentembed_errorcode) - The client callback fails to be executed.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - This operation is not supported because the application is in      the DLP sandbox.</li>          </ul> |

### OH_ContentEmbed_Extension_CallbackToOnEditingFinished()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnEditingFinished(ContentEmbed_ObjectHandle object, bool dataModified)
```

**Description**

Registers the callback function for finishing editing an OE document.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance. |
| bool dataModified | Indicates whether the document data has been modified. The value true indicates that the file is modified, and the value false indicates that the file is not modified. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Failed to check the parameter.</li>      <li>[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode) - A null pointer is returned.</li>      <li>[CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED](capi-content-embed-common-h.md#contentembed_errorcode) - The client callback is not registered.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_CLIENT_CALLBACK_FAILED](capi-content-embed-common-h.md#contentembed_errorcode) - The client callback fails to be executed.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - This operation is not supported because the application is in      the DLP sandbox.</li>          </ul> |

### OH_ContentEmbed_Extension_CallbackToOnExtensionStopped()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnExtensionStopped(ContentEmbed_ExtensionInstanceHandle instance)
```

**Description**

Stops the callback function of the OE Extension that is associated with all client-side OE objects and registered by the OE Extension.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance object. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - Operations are successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Failed to check the parameter.</li>      <li>[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode) - A null pointer is returned.</li>      <li>[CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED](capi-content-embed-common-h.md#contentembed_errorcode) - The client callback is not registered.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_CLIENT_CALLBACK_FAILED](capi-content-embed-common-h.md#contentembed_errorcode) - Failed to execute the client callback.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - This operation is not supported because the application is in      the DLP sandbox.</li>          </ul> |

### OH_ContentEmbed_Extension_SetSnapshot()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_SetSnapshot(ContentEmbed_ObjectHandle object, OH_PixelmapNative *pixelMap)
```

**Description**

Sets the snapshot image of the OE document associated with the client-side OE object.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance. |
| OH_PixelmapNative *pixelMap | Pixel map object of the document snapshot. For details, see {@link OH_PixelmapNative}. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Failed to check the parameter.</li>      <li>[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode) - A null pointer is returned.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is not supported because the app is in the DLP sandbox.</li>      <li>[CE_ERR_IMAGE_PACKER_OPERATION_FAILED](capi-content-embed-common-h.md#contentembed_errorcode) - Failed to perform the image operation.</li>          </ul> |

### OH_ContentEmbed_Extension_ContextStartSelfUIAbility()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextStartSelfUIAbility(ContentEmbed_ExtensionContextHandle context, AbilityBase_Want *want)
```

**Description**

Starts the {@link UIAbility} of the current instance using the OE Extension context.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) context | Pointer to the context object of the OE Extension. |
| AbilityBase_Want *want | Parameter passed when the UIAbility is started. For details, see {@link AbilityBase_Want}. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Failed to check the parameter.</li>      <li>[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode) - A null pointer is returned.</li>      <li>[CE_ERR_SYSTEM_ABNORMAL](capi-content-embed-common-h.md#contentembed_errorcode) - The system service is abnormal.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - This operation is not supported because the application is in      the DLP sandbox.</li>          </ul> |

### OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions(ContentEmbed_ExtensionContextHandle context, AbilityBase_Want *want, AbilityRuntime_StartOptions *options)
```

**Description**

Starts the {@link UIAbility} of the OE Extension context using the start options.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) context | Pointer to the OE Extension context object. |
| AbilityBase_Want *want | Parameter passed when the UIAbility is started. For details, see {@link AbilityBase_Want}. |
| AbilityRuntime_StartOptions *options | Additional options for starting the UIAbility. For details, see {@link AbilityRuntime_StartOptions}. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Failed to check the parameter.</li>      <li>[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode) - A null pointer is returned.</li>      <li>[CE_ERR_SYSTEM_ABNORMAL](capi-content-embed-common-h.md#contentembed_errorcode) - The system service is abnormal.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - This operation is not supported because the application is in      the DLP sandbox.</li>          </ul> |

### OH_ContentEmbed_Extension_ContextTerminateAbility()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextTerminateAbility(ContentEmbed_ExtensionContextHandle context)
```

**Description**

Destroys the OE Extension.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) context | Pointer to the OE Extension context object. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - Operations are successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Parameter check failed.</li>      <li>[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode) - A null pointer is returned.</li>      <li>[CE_ERR_SYSTEM_ABNORMAL](capi-content-embed-common-h.md#contentembed_errorcode) - The system service is abnormal.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - This operation is not supported because the application is in      the DLP sandbox.</li>          </ul> |


