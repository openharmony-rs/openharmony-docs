# content_embed_extension.h

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->

## Overview

Defines the data structures and operation APIs related to the OE Extension of the server application.

**Header file**: <ContentEmbedKit/content_embed/content_embed_extension.h>

**Library**: libcontent_embed_ndk.so

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Related module**: [ContentEmbed](capi-contentembed.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) | ContentEmbed_Document | Defines the structure type of an OE document. Encapsulates the metadata, content, and storage structure of the embedded document.|
| [ContentEmbed_ExtensionContext](capi-contentembed-contentembed-extensioncontext.md) | ContentEmbed_ExtensionContext | Defines the structure type of the OE Extension context.|
| [ContentEmbed_ExtensionContext*](capi-contentembed-contentembed-extensioncontext8h.md) | ContentEmbed_ExtensionContextHandle | Defines the pointer type of the OE Extension context object.|
| [ContentEmbed_ExtensionInstance](capi-contentembed-contentembed-extensioninstance.md) | ContentEmbed_ExtensionInstance | Declares the structure type of an OE Extension instance. Manages the lifecycle of extensions, and core functions such as callback registration and association with client-side OE objects.|
| [ContentEmbed_ExtensionInstance*](capi-contentembed-contentembed-extensioninstance8h.md) | ContentEmbed_ExtensionInstanceHandle | Declares the pointer type of an OE Extension instance object.|
| [ContentEmbed_Object](capi-contentembed-contentembed-object.md) | ContentEmbed_Object | Declares the ContentEmbed_Object structure type. Points to the program object (server-side OE object for short) that encapsulates and edits the OE document on the server.|
| [ContentEmbed_Object*](capi-contentembed-contentembed-object8h.md) | ContentEmbed_ObjectHandle | Declares the pointer type of a ContentEmbed_Object object.|

### Function

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContentEmbedContext(ContentEmbed_ExtensionInstanceHandle ceInstance, ContentEmbed_ExtensionContextHandle *ceContext)](#oh_contentembed_extension_getcontentembedcontext) | - | Obtains the corresponding OE Extension context object from the OE Extension instance.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContext(ContentEmbed_ExtensionContextHandle ceContext, AbilityRuntime_ContextHandle *context)](#oh_contentembed_extension_getcontext) | - | Obtains the AbilityRuntime context from the OE Extension context.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetExtensionInstance(AbilityRuntime_ExtensionInstanceHandle baseInstance, ContentEmbed_ExtensionInstanceHandle *ceInstance)](#oh_contentembed_extension_getextensioninstance) | - | Obtains the corresponding OE Extension instance from the ExtensionAbility base class instance.|
| [typedef void (\*OH_ContentEmbed_Extension_OnCreateFunc)(ContentEmbed_ExtensionInstanceHandle instance, AbilityBase_Want *want)](#oh_contentembed_extension_oncreatefunc) | OH_ContentEmbed_Extension_OnCreateFunc | Type of the lifecycle function when an OE Extension instance is created.<br> You need to implement this function and register it with the OE Extension instance through [OH_ContentEmbed_Extension_RegisterOnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeroncreatefunc).|
| [typedef void (\*OH_ContentEmbed_Extension_OnDestroyFunc)(ContentEmbed_ExtensionInstanceHandle instance)](#oh_contentembed_extension_ondestroyfunc) | OH_ContentEmbed_Extension_OnDestroyFunc | Lifecycle function type when an OE Extension instance is destroyed.<br> You need to implement this function and register it with the OE Extension instance through [OH_ContentEmbed_Extension_RegisterOnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondestroyfunc).|
| [typedef void (\*OH_ContentEmbed_Extension_OnObjectAttachFunc)(ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_onobjectattachfunc) | OH_ContentEmbed_Extension_OnObjectAttachFunc | This callback function is triggered when the client OE object is connected to the OE Extension instance. It is used to perform the initialization operation after the server OE object is associated.<br> You need to implement this function and register it with the OE Extension instance through [OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectattachfunc).|
| [typedef void (\*OH_ContentEmbed_Extension_OnObjectDetachFunc)(ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_onobjectdetachfunc) | OH_ContentEmbed_Extension_OnObjectDetachFunc | This callback function is triggered when the client OE object is disconnected from the OE Extension instance. It is used to perform the cleanup operation after the server OE object is disconnected.<br> You need to implement this function and register it with the OE Extension instance through [OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectdetachfunc).|
| [typedef void (\*OH_ContentEmbed_Extension_OnWriteToDataStreamFunc)(ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_onwritetodatastreamfunc) | OH_ContentEmbed_Extension_OnWriteToDataStreamFunc | This callback function is triggered when the server OE object writes data to the OE document.<br> You need to implement this function and register it with the server OE object through [OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronwritetodatastreamfunc).|
| [typedef void (\*OH_ContentEmbed_Extension_OnGetSnapshotFunc)(ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_ongetsnapshotfunc) | OH_ContentEmbed_Extension_OnGetSnapshotFunc | Callback function type when the client's OE object requests to obtain the OE document snapshot.<br> You need to implement this function and register it with the server's OE object through [OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetsnapshotfunc).|
| [typedef void (\*OH_ContentEmbed_Extension_OnDoEditFunc)(ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_ondoeditfunc) | OH_ContentEmbed_Extension_OnDoEditFunc | Callback function type when the client's OE object requests to edit the OE document.<br> You need to implement this function and register it with the server's OE object through [OH_ContentEmbed_Extension_RegisterOnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondoeditfunc).|
| [typedef void (\*OH_ContentEmbed_Extension_OnGetEditStatusFunc)(ContentEmbed_ObjectHandle object, bool *isEditing, bool *isModified)](#oh_contentembed_extension_ongeteditstatusfunc) | OH_ContentEmbed_Extension_OnGetEditStatusFunc | Callback function type when the client's OE object requests the editing state of the OE document.<br> You need to implement this function and register it with the server-side OE object through [OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongeteditstatusfunc).|
| [typedef void (\*OH_ContentEmbed_Extension_OnGetCapabilityFunc)(ContentEmbed_ObjectHandle object, uint32_t *bitmask)](#oh_contentembed_extension_ongetcapabilityfunc) | OH_ContentEmbed_Extension_OnGetCapabilityFunc | Callback function used when the client-side OE object queries the capabilities supported by the OE Extension instance.<br> You need to implement this function and register it with the server-side OE object through [OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetcapabilityfunc).|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnCreateFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnCreateFunc onCreateFunc)](#oh_contentembed_extension_registeroncreatefunc) | - | Lifecycle function registered when an OE Extension instance is created.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnDestroyFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnDestroyFunc onDestroyFunc)](#oh_contentembed_extension_registerondestroyfunc) | - | Registers the lifecycle function for destroying an OE Extension instance.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnObjectAttachFunc onObjectAttachFunc)](#oh_contentembed_extension_registeronobjectattachfunc) | - | Registers the callback function for connecting to the client OE object.<br> You can call [OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_unregisteronobjectattachfunc) to cancel the registration.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc(ContentEmbed_ExtensionInstanceHandle instance)](#oh_contentembed_extension_unregisteronobjectattachfunc) | - | Cancels the registration of the callback function for connecting to the client OE object.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnObjectDetachFunc onObjectDetachFunc)](#oh_contentembed_extension_registeronobjectdetachfunc) | - | Registers the callback function for disconnecting the client from the OE object.<br> You can call [OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_unregisteronobjectdetachfunc) to cancel the registration.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc(ContentEmbed_ExtensionInstanceHandle instance)](#oh_contentembed_extension_unregisteronobjectdetachfunc) | - | Cancels the registration of the callback function for disconnecting the client from the OE object.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnWriteToDataStreamFunc onWriteToDataStreamFunc)](#oh_contentembed_extension_registeronwritetodatastreamfunc) | - | Registers the callback function for writing the OE document data stream to the server-side OE object.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetSnapshotFunc onGetSnapshotFunc)](#oh_contentembed_extension_registerongetsnapshotfunc) | - | Registers the callback function for the client to obtain the snapshot of an OE document.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnDoEditFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnDoEditFunc onDoEditFunc)](#oh_contentembed_extension_registerondoeditfunc) | - | Registers the callback function for the client to edit an OE document.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetEditStatusFunc onGetEditStatusFunc)](#oh_contentembed_extension_registerongeteditstatusfunc) | - | Registers the callback function for the client to obtain the editing state of an OE document.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetCapabilityFunc onGetCapabilityFunc)](#oh_contentembed_extension_registerongetcapabilityfunc) | - | Callback function invoked when the registered client object queries the capability of the OE Extension instance.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContentEmbedDocument(ContentEmbed_ObjectHandle object, ContentEmbed_Document **ceDocument)](#oh_contentembed_extension_getcontentembeddocument) | - | Obtains the OE document instance associated with the server object.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnUpdate(ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_callbacktoonupdate) | - | Callback function invoked when the OE document associated with the registered client object is updated.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnError(ContentEmbed_ObjectHandle object, ContentEmbed_ErrorCode code)](#oh_contentembed_extension_callbacktoonerror) | - | Callback function invoked when an error occurs in the OE document associated with the registered client object.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnEditingFinished(ContentEmbed_ObjectHandle object, bool dataModified)](#oh_contentembed_extension_callbacktooneditingfinished) | - | Callback function invoked when the editing of the OE document associated with the registered client object is completed.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnExtensionStopped(ContentEmbed_ExtensionInstanceHandle instance)](#oh_contentembed_extension_callbacktoonextensionstopped) | - | Callback function that is triggered when the OE Extension associated with all client OE objects stops.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_SetSnapshot(ContentEmbed_ObjectHandle object, OH_PixelmapNative *pixelMap)](#oh_contentembed_extension_setsnapshot) | - | Sets the snapshot image of the OE document associated with the client OE object.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextStartSelfUIAbility(ContentEmbed_ExtensionContextHandle context, AbilityBase_Want *want)](#oh_contentembed_extension_contextstartselfuiability) | - | Starts the [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md#uiability) of the OE Extension using the OE Extension context.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions(ContentEmbed_ExtensionContextHandle context, AbilityBase_Want *want, AbilityRuntime_StartOptions *options)](#oh_contentembed_extension_contextstartselfuiabilitywithstartoptions) | - | Starts the [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md#uiability) of the OE Extension context using the startup option.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextTerminateAbility(ContentEmbed_ExtensionContextHandle context)](#oh_contentembed_extension_contextterminateability) | - | Destroys the OE Extension.|

## Function Description

### OH_ContentEmbed_Extension_GetContentEmbedContext()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContentEmbedContext(ContentEmbed_ExtensionInstanceHandle ceInstance, ContentEmbed_ExtensionContextHandle *ceContext)
```

**Description**

Obtains the corresponding OE Extension context object from the OE Extension instance.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) ceInstance | Pointer to the OE Extension instance object.|
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) *ceContext | Output parameter. After the function is successfully called, this pointer points to the context object of the OE Extension instance.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The specific error code is returned as follows:<br>     CE_ERR_OK: indicates that the operation is successful.<br>     CE_ERR_PARAM_INVALID: Parameter check failed.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: The operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Extension_GetContext()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContext(ContentEmbed_ExtensionContextHandle ceContext, AbilityRuntime_ContextHandle *context)
```

**Description**

Obtains the AbilityRuntime context from the OE Extension context.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) ceContext | Pointer to the OE Extension context object.|
| AbilityRuntime_ContextHandle *context | Output parameter. After the call is successful, this pointer points to the AbilityRuntime_ContextHandle context object.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Parameter check failed.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: The operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Extension_GetExtensionInstance()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetExtensionInstance(AbilityRuntime_ExtensionInstanceHandle baseInstance, ContentEmbed_ExtensionInstanceHandle *ceInstance)
```

**Description**

Obtains the corresponding OE Extension instance from the ExtensionAbility base class instance.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| AbilityRuntime_ExtensionInstanceHandle baseInstance | AbilityRuntime_ExtensionInstanceHandle instance.|
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) *ceInstance | Output parameter. After the call is successful, this pointer points to the OE Extension instance object.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: The operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Extension_OnCreateFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnCreateFunc)(ContentEmbed_ExtensionInstanceHandle instance, AbilityBase_Want *want)
```

**Description**

Indicates the lifecycle function type when an OE Extension instance is created.<br> You need to implement this function and register it with the OE Extension instance through [OH_ContentEmbed_Extension_RegisterOnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeroncreatefunc).

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance object.|
| [AbilityBase_Want](../apis-ability-kit/capi-abilitybase-want.md) \*want | Pointer to the [AbilityBase_Want](../apis-ability-kit/capi-abilitybase-want.md) instance.|

### OH_ContentEmbed_Extension_OnDestroyFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnDestroyFunc)(ContentEmbed_ExtensionInstanceHandle instance)
```

**Description**

Indicates the lifecycle function type when an OE Extension instance is destroyed.<br> You need to implement this function and register it with the OE Extension instance through [OH_ContentEmbed_Extension_RegisterOnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondestroyfunc).

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance object.|

### OH_ContentEmbed_Extension_OnObjectAttachFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnObjectAttachFunc)(ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object)
```

**Description**

This callback function is triggered when the client's OE object is connected to the OE Extension instance. It is used to perform the initialization operation after the server's OE object is associated.<br> You need to implement this function and register it with the OE Extension instance through [OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectattachfunc).

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance object.|
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|

### OH_ContentEmbed_Extension_OnObjectDetachFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnObjectDetachFunc)(ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object)
```

**Description**

This callback function is triggered when the client disconnects from the OE Extension instance, and is used to perform cleanup operations after the server disconnects from the OE Extension instance.<br> You need to implement this function and register it with the OE Extension instance through [OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectdetachfunc).

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance object.|
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|

### OH_ContentEmbed_Extension_OnWriteToDataStreamFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnWriteToDataStreamFunc)(ContentEmbed_ObjectHandle object)
```

**Description**

Callback function type used when the server-side OE object writes data to the OE document.<br> You need to implement this function and register it with the server-side OE object through [OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronwritetodatastreamfunc).

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|

### OH_ContentEmbed_Extension_OnGetSnapshotFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnGetSnapshotFunc)(ContentEmbed_ObjectHandle object)
```

**Description**

Callback function type used when the client-side OE object requests to obtain the OE document snapshot.<br> You need to implement this function and register it with the server-side OE object through [OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetsnapshotfunc).

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|

### OH_ContentEmbed_Extension_OnDoEditFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnDoEditFunc)(ContentEmbed_ObjectHandle object)
```

**Description**

Callback function type when the client's OE object requests to edit an OE document.<br> You need to implement this function and register it with the server's OE object through [OH_ContentEmbed_Extension_RegisterOnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondoeditfunc).

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|

### OH_ContentEmbed_Extension_OnGetEditStatusFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnGetEditStatusFunc)(ContentEmbed_ObjectHandle object, bool *isEditing, bool *isModified)
```

**Description**

Callback function type when the client's OE object requests the editing state of an OE document.<br> You need to implement this function and register it with the server's OE object through [OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongeteditstatusfunc).

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| bool \*isEditing | Output parameter. Indicates whether the OE document is being edited. The value true indicates that the document is being edited, and the value false indicates that the document is not being edited.|
| bool \*isModified | Output parameter. Indicates whether the OE document has been modified. The value true indicates that the document has been modified, and the value false indicates that the document has not been modified.|

### OH_ContentEmbed_Extension_OnGetCapabilityFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnGetCapabilityFunc)(ContentEmbed_ObjectHandle object, uint32_t *bitmask)
```

**Description**

Indicates the callback function type when the client queries the capabilities supported by the OE Extension instance.<br> You need to implement this function and register it with the server-side OE object through [OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetcapabilityfunc).

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| uint32_t \*bitmask | Output parameter, which indicates the capabilities supported by the OE Extension instance. The value is a combination of the values in [ContentEmbed_CapabilityCode](capi-content-embed-common-h.md#contentembed_capabilitycode).|

### OH_ContentEmbed_Extension_RegisterOnCreateFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnCreateFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnCreateFunc onCreateFunc)
```

**Description**

Registers the lifecycle function for creating an OE Extension instance.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance object.|
| [OH_ContentEmbed_Extension_OnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_oncreatefunc) onCreateFunc | [OH_ContentEmbed_Extension_OnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_oncreatefunc) lifecycle function to be registered.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: The parameter check fails.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Extension_RegisterOnDestroyFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnDestroyFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnDestroyFunc onDestroyFunc)
```

**Description**

Registers the lifecycle function for destroying an OE Extension instance.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance object.|
| [OH_ContentEmbed_Extension_OnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ondestroyfunc) onDestroyFunc | [OH_ContentEmbed_Extension_OnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ondestroyfunc) lifecycle function to be registered.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: The parameter check fails.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnObjectAttachFunc onObjectAttachFunc)
```

**Description**

Registers the callback function for connecting to the client's OE object.<br> You can call [OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_unregisteronobjectattachfunc) to deregister the callback function.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance object.|
| [OH_ContentEmbed_Extension_OnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onobjectattachfunc) onObjectAttachFunc | [OH_ContentEmbed_Extension_OnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onobjectattachfunc) callback function to be registered.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: The parameter check fails.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: The operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc(ContentEmbed_ExtensionInstanceHandle instance)
```

**Description**

Cancels the registration of the callback function for disconnecting the client from the OE object.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance object.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: The operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnObjectDetachFunc onObjectDetachFunc)
```

**Description**

Registers the callback function for disconnecting the client from the OE object.<br> You can call [OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_unregisteronobjectdetachfunc) to cancel the registration.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the instance object of the OpenHarmony Extension.|
| [OH_ContentEmbed_Extension_OnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onobjectdetachfunc) onObjectDetachFunc | [OH_ContentEmbed_Extension_OnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onobjectdetachfunc) callback function to be registered.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc(ContentEmbed_ExtensionInstanceHandle instance)
```

**Description**

Cancels the callback function for disconnecting the client from the OE object.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance object.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: The parameter check fails.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnWriteToDataStreamFunc onWriteToDataStreamFunc)
```

**Description**

Registers the callback function for the server to write data streams to the OE document.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| [OH_ContentEmbed_Extension_OnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onwritetodatastreamfunc) onWriteToDataStreamFunc | [OH_ContentEmbed_Extension_OnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onwritetodatastreamfunc) callback function to be registered.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The specific error code is returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetSnapshotFunc onGetSnapshotFunc)
```

**Description**

Registers the callback function for obtaining the OE document snapshot when the client requests to obtain the OE document snapshot.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| [OH_ContentEmbed_Extension_OnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongetsnapshotfunc) onGetSnapshotFunc | [OH_ContentEmbed_Extension_OnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongetsnapshotfunc) callback function to be registered.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The specific error code is returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Extension_RegisterOnDoEditFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnDoEditFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnDoEditFunc onDoEditFunc)
```

**Description**

Registers the callback function for editing an OE document when the client requests to edit the OE document.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| [OH_ContentEmbed_Extension_OnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ondoeditfunc) onDoEditFunc | [OH_ContentEmbed_Extension_OnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ondoeditfunc) callback function to be registered.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The specific error code is returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetEditStatusFunc onGetEditStatusFunc)
```

**Description**

Registers the callback function for requesting the editing state of an OE document from the client.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| [OH_ContentEmbed_Extension_OnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongeteditstatusfunc) onGetEditStatusFunc | [OH_ContentEmbed_Extension_OnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongeteditstatusfunc) callback function to be registered.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The specific error code is returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetCapabilityFunc onGetCapabilityFunc)
```

**Description**

Registers the callback function for querying whether the OE Extension instance supports the capability of the client's OE object.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| [OH_ContentEmbed_Extension_OnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongetcapabilityfunc) onGetCapabilityFunc | [OH_ContentEmbed_Extension_OnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongetcapabilityfunc) callback function to be registered.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The specific error code is returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Extension_GetContentEmbedDocument()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContentEmbedDocument(ContentEmbed_ObjectHandle object, ContentEmbed_Document **ceDocument)
```

**Description**

Obtains the instance of the OE document associated with the server-side OE object.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) **ceDocument | Output parameter. After the call is successful, this pointer points to the associated OE document instance.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: The parameter check fails.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: The operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Extension_CallbackToOnUpdate()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnUpdate(ContentEmbed_ObjectHandle object)
```

**Description**

Triggers the callback function for updating the OE document to register the client's OE object.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: The parameter check fails.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED: The client callback is not registered.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_CLIENT_CALLBACK_FAILED: The client callback fails to be executed.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Extension_CallbackToOnError()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnError(ContentEmbed_ObjectHandle object, ContentEmbed_ErrorCode code)
```

**Description**

Trigger the callback function of the error in the OE document that triggers the registration of the client's OE object.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) code | Error code. For details, see [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode).|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: The parameter check fails.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED: The client callback is not registered.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_CLIENT_CALLBACK_FAILED: The client callback fails to be executed.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Extension_CallbackToOnEditingFinished()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnEditingFinished(ContentEmbed_ObjectHandle object, bool dataModified)
```

**Description**

Registers the callback function for finishing editing an OE document.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| bool dataModified | Indicates whether the document data has been modified. The value true indicates that the file is modified, and the value false indicates that the file is not modified.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED: The client callback is not registered.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_CLIENT_CALLBACK_FAILED: The client callback fails to be executed.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Extension_CallbackToOnExtensionStopped()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnExtensionStopped(ContentEmbed_ExtensionInstanceHandle instance)
```

**Description**

Stops the callback function of the OE Extension that is associated with all client-side OE objects and registered by the OE Extension.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance object.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The following error codes are returned:<br>     CE_ERR_OK: Operations are successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED: The client callback is not registered.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_CLIENT_CALLBACK_FAILED: Failed to execute the client callback.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Extension_SetSnapshot()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_SetSnapshot(ContentEmbed_ObjectHandle object, OH_PixelmapNative *pixelMap)
```

**Description**

Sets the snapshot image of the OE document associated with the client-side OE object.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| [OH_PixelmapNative](../apis-arkgraphics2d/capi-drawing-oh-pixelmapnative.md) *pixelMap | Pixel map object of the document snapshot. For details, see [OH_PixelmapNative](../apis-arkgraphics2d/capi-drawing-oh-pixelmapnative.md).|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The specific error code is returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: The operation is not supported because the app is in the DLP sandbox.<br>     CE_ERR_IMAGE_PACKER_OPERATION_FAILED: Failed to perform the image operation.|

### OH_ContentEmbed_Extension_ContextStartSelfUIAbility()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextStartSelfUIAbility(ContentEmbed_ExtensionContextHandle context, AbilityBase_Want *want)
```

**Description**

Starts the [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md#uiability) of the current instance using the OE Extension context.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) context | Pointer to the context object of the OE Extension.|
| [AbilityBase_Want](../apis-ability-kit/capi-abilitybase-want.md) *want | Parameter passed when the UIAbility is started. For details, see [AbilityBase_Want](../apis-ability-kit/capi-abilitybase-want.md).|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The specific error code is returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_SYSTEM_ABNORMAL: The system service is abnormal.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions(ContentEmbed_ExtensionContextHandle context, AbilityBase_Want *want, AbilityRuntime_StartOptions *options)
```

**Description**

Starts the [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md#uiability) of the OE Extension context using the start options.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) context | Pointer to the OE Extension context object.|
| [AbilityBase_Want](../apis-ability-kit/capi-abilitybase-want.md) *want | Parameter passed when the UIAbility is started. For details, see [AbilityBase_Want](../apis-ability-kit/capi-abilitybase-want.md).|
| [AbilityRuntime_StartOptions](../apis-ability-kit/capi-abilityruntime-startoptions.md) *options | Additional options for starting the UIAbility. For details, see [AbilityRuntime_StartOptions](../apis-ability-kit/capi-abilityruntime-startoptions.md).|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The specific error code is returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_SYSTEM_ABNORMAL: The system service is abnormal.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Extension_ContextTerminateAbility()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextTerminateAbility(ContentEmbed_ExtensionContextHandle context)
```

**Description**

Destroys the OE Extension.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) context | Pointer to the OE Extension context object.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The following error codes are returned:<br>     CE_ERR_OK: Operations are successful.<br>     CE_ERR_PARAM_INVALID: Parameter check failed.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_SYSTEM_ABNORMAL: The system service is abnormal.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|
