# content_embed_extension.h

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->

## Overview

Defines the data structures and operation APIs related to the OE extension in server apps and provides capabilities such as OE extension instance lifecycle management, client OE object association and callback registration, and snapshot obtaining and editing. This module is applicable to document embedding and editing on the server.

**File to include:** <ContentEmbedKit/content_embed/content_embed_extension.h>

**Library:** libcontent_embed_ndk.so

**System capability:** SystemCapability.ContentEmbed.ObjectEditor

**Since:** 24

**Related module:** [ContentEmbed](capi-contentembed.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) | ContentEmbed_Document | Defines the struct of an OE document. This struct encapsulates the metadata, content, and storage structure of an embedded document. It is used to manage the data of embedded documents in a unified manner within an app, facilitating access, parsing, and storage of the embedded documents.<br>You can select a method based on the data source:<br>Use [OH_ContentEmbed_CreateDocumentByOEid](capi-content-embed-document-h.md#oh_contentembed_createdocumentbyoeid) if you have the OEID.<br>Use [OH_ContentEmbed_CreateDocumentByFile](capi-content-embed-document-h.md#oh_contentembed_createdocumentbyfile) if you have the source file and need to embed or link it.<br>Use [OH_ContentEmbed_LoadDocumentFromFile](capi-content-embed-document-h.md#oh_contentembed_loaddocumentfromfile) if you have a saved OE file.|
| [ContentEmbed_ExtensionContext](capi-contentembed-contentembed-extensioncontext.md) | ContentEmbed_ExtensionContext | Defines the struct type of the OE extension context.|
| [ContentEmbed_ExtensionContext*](capi-contentembed-contentembed-extensioncontext8h.md) | ContentEmbed_ExtensionContextHandle | Defines the pointer type of the OE extension context object. This pointer object is used to carry and manage the running context of the OE extension in the **ContentEmbed** extension process.<br>You can obtain the context from the OE extension instance by calling [OH_ContentEmbed_Extension_GetContentEmbedContext](capi-content-embed-extension-h.md#oh_contentembed_extension_getcontentembedcontext). You can use [OH_ContentEmbed_Extension_GetContext](capi-content-embed-extension-h.md#oh_contentembed_extension_getcontext) to obtain the AbilityRuntime context, start the UIAbility using [OH_ContentEmbed_Extension_ContextStartSelfUIAbility](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiability) or [OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiabilitywithstartoptions), and destroy the OE extension using [OH_ContentEmbed_Extension_ContextTerminateAbility](capi-content-embed-extension-h.md#oh_contentembed_extension_contextterminateability).|
| [ContentEmbed_ExtensionInstance](capi-contentembed-contentembed-extensioninstance.md) | ContentEmbed_ExtensionInstance | Defines the struct type of the OE extension instance. This method can be used to manage core functions such as the lifecycle of the extension, callback registration, and association with the client OE object. This method is applicable to scenarios where server apps need to embed OE extension capabilities and complete lifecycle synchronization, callback listening, and object association and binding between the extension and the client OE document.|
| [ContentEmbed_ExtensionInstance*](capi-contentembed-contentembed-extensioninstance8h.md) | ContentEmbed_ExtensionInstanceHandle | Defines the pointer type of the OE extension instance. In the **OH_AbilityRuntime_OnNativeExtensionCreate** function, you need to obtain the OE extension instance when the OE extension is started by calling [OH_ContentEmbed_Extension_GetExtensionInstance](capi-content-embed-extension-h.md#oh_contentembed_extension_getextensioninstance).|
| [ContentEmbed_Object](capi-contentembed-contentembed-object.md) | ContentEmbed_Object | Defines the **ContentEmbed_Object** struct. This struct points to the program object (server OE object for short) that encapsulates the document embedding and editing functions of the OE document on the server.|
| [ContentEmbed_Object*](capi-contentembed-contentembed-object8h.md) | ContentEmbed_ObjectHandle | Defines a struct for the pointer to a **ContentEmbed_Object** object. When the client connects to the server, the system creates an instance of this object, calls back the **OH_ContentEmbed_Extension_OnObjectAttachFunc** function registered by [OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectattachfunc), and passes the instance pointer of this type.|

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContentEmbedContext(ContentEmbed_ExtensionInstanceHandle ceInstance, ContentEmbed_ExtensionContextHandle *ceContext)](#oh_contentembed_extension_getcontentembedcontext) | - | Obtains the OE extension context object from the OE extension instance. You can use [OH_ContentEmbed_Extension_GetContext](capi-content-embed-extension-h.md#oh_contentembed_extension_getcontext) to obtain the AbilityRuntime context, start the UIAbility using [OH_ContentEmbed_Extension_ContextStartSelfUIAbility](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiability) or [OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiabilitywithstartoptions), and destroy the OE extension using [OH_ContentEmbed_Extension_ContextTerminateAbility](capi-content-embed-extension-h.md#oh_contentembed_extension_contextterminateability).|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContext(ContentEmbed_ExtensionContextHandle ceContext, AbilityRuntime_ContextHandle *context)](#oh_contentembed_extension_getcontext) | - | Obtains the AbilityRuntime context from the OE extension context.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetExtensionInstance(AbilityRuntime_ExtensionInstanceHandle baseInstance, ContentEmbed_ExtensionInstanceHandle *ceInstance)](#oh_contentembed_extension_getextensioninstance) | - | Obtains the OE extension instance from the ExtensionAbility base class instance.<br>You are advised to call this method in the [OH_AbilityRuntime_OnNativeExtensionCreate](../apis-ability-kit/capi-extension-ability-h.md#oh_abilityruntime_onnativeextensioncreate) function. After obtaining the instance, call [OH_ContentEmbed_Extension_RegisterOnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeroncreatefunc) and [OH_ContentEmbed_Extension_RegisterOnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondestroyfunc) to register the OE extension lifecycle callback functions.|
| [typedef void (\*OH_ContentEmbed_Extension_OnCreateFunc)(ContentEmbed_ExtensionInstanceHandle instance, AbilityBase_Want *want)](#oh_contentembed_extension_oncreatefunc) | OH_ContentEmbed_Extension_OnCreateFunc | Defines the lifecycle function when the OE extension instance is created.<br>You need to implement this function and register it with the OE extension instance through [OH_ContentEmbed_Extension_RegisterOnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeroncreatefunc).|
| [typedef void (\*OH_ContentEmbed_Extension_OnDestroyFunc)(ContentEmbed_ExtensionInstanceHandle instance)](#oh_contentembed_extension_ondestroyfunc) | OH_ContentEmbed_Extension_OnDestroyFunc | Defines the lifecycle function when the OE extension instance is destroyed.<br>You need to implement this function and register it with the OE extension instance through [OH_ContentEmbed_Extension_RegisterOnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondestroyfunc).|
| [typedef void (\*OH_ContentEmbed_Extension_OnObjectAttachFunc)(ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_onobjectattachfunc) | OH_ContentEmbed_Extension_OnObjectAttachFunc | Defines the callback function used when the client OE object is connected to the OE extension instance. This callback function is used to perform the initialization operation after the server OE object is associated.<br>You need to implement this function and register it with the OE extension instance through [OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectattachfunc). In this callback, you need to call the [OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronwritetodatastreamfunc), [OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetcapabilityfunc), [OH_ContentEmbed_Extension_RegisterOnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondoeditfunc), [OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetsnapshotfunc), and [OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongeteditstatusfunc) functions to register the callback functions for responding to the OE object request from the client.|
| [typedef void (\*OH_ContentEmbed_Extension_OnObjectDetachFunc)(ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_onobjectdetachfunc) | OH_ContentEmbed_Extension_OnObjectDetachFunc | Defines the callback function used when the client OE object is disconnected from the OE extension instance. This callback function is used to perform the cleanup operation after the server OE object is disconnected.<br>You need to implement this function and register it with the OE extension instance through [OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectdetachfunc).|
| [typedef void (\*OH_ContentEmbed_Extension_OnWriteToDataStreamFunc)(ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_onwritetodatastreamfunc) | OH_ContentEmbed_Extension_OnWriteToDataStreamFunc | Defines the callback function used when the server OE object writes data to the OE document stream.<br>You need to implement this function and register it with the server OE object through [OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronwritetodatastreamfunc).|
| [typedef void (\*OH_ContentEmbed_Extension_OnGetSnapshotFunc)(ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_ongetsnapshotfunc) | OH_ContentEmbed_Extension_OnGetSnapshotFunc | Defines the callback function used when the client OE object requests to obtain the snapshot of an OE document.<br>You need to implement this function and register it with the server OE object through [OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetsnapshotfunc).<br>In this callback, you need to call [OH_ContentEmbed_Extension_SetSnapshot](capi-content-embed-extension-h.md#oh_contentembed_extension_setsnapshot) to set the snapshot image of the OE document to respond to the client's request to obtain the snapshot.|
| [typedef void (\*OH_ContentEmbed_Extension_OnDoEditFunc)(ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_ondoeditfunc) | OH_ContentEmbed_Extension_OnDoEditFunc | Defines the callback function used when the client OE object requests to edit an OE document.<br>You need to implement this function and register it with the server OE object through [OH_ContentEmbed_Extension_RegisterOnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondoeditfunc).<br>In this callback, you can start the UIAbility of your app for editing through [OH_ContentEmbed_Extension_ContextStartSelfUIAbility](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiability) and [OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiabilitywithstartoptions). After the editing is complete, you need to call [OH_ContentEmbed_Extension_CallbackToOnEditingFinished](capi-content-embed-extension-h.md#oh_contentembed_extension_callbacktooneditingfinished) to notify the client.|
| [typedef void (\*OH_ContentEmbed_Extension_OnGetEditStatusFunc)(ContentEmbed_ObjectHandle object, bool *isEditing, bool *isModified)](#oh_contentembed_extension_ongeteditstatusfunc) | OH_ContentEmbed_Extension_OnGetEditStatusFunc | Defines the callback function used when the client OE object requests the editing state of an OE document.<br>You need to implement this function and register it with the server OE object through [OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongeteditstatusfunc).|
| [typedef void (\*OH_ContentEmbed_Extension_OnGetCapabilityFunc)(ContentEmbed_ObjectHandle object, uint32_t *bitmask)](#oh_contentembed_extension_ongetcapabilityfunc) | OH_ContentEmbed_Extension_OnGetCapabilityFunc | Defines the callback function used when the client OE object queries the capabilities supported by the OE extension instance.<br>You need to implement this function and register it with the server OE object through [OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetcapabilityfunc).|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnCreateFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnCreateFunc onCreateFunc)](#oh_contentembed_extension_registeroncreatefunc) | - | Registers the lifecycle function when the OE extension instance is created.<br>The callback cannot be unregistered after being registered and remains valid throughout the instance lifecycle.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnDestroyFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnDestroyFunc onDestroyFunc)](#oh_contentembed_extension_registerondestroyfunc) | - | Registers the lifecycle function when the OE extension instance is destroyed.<br>The callback cannot be unregistered after being registered and remains valid throughout the instance lifecycle.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnObjectAttachFunc onObjectAttachFunc)](#oh_contentembed_extension_registeronobjectattachfunc) | - | Registers the callback function for connecting to the client OE object.<br>You can call [OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_unregisteronobjectattachfunc) to unregister the callback.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc(ContentEmbed_ExtensionInstanceHandle instance)](#oh_contentembed_extension_unregisteronobjectattachfunc) | - | Unregisters the callback function for connecting to the client OE object. You can call [OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectattachfunc) to register the callback again.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnObjectDetachFunc onObjectDetachFunc)](#oh_contentembed_extension_registeronobjectdetachfunc) | - | Registers the callback function for disconnecting from the client OE object.<br>You can call [OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_unregisteronobjectdetachfunc) to unregister the callback.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc(ContentEmbed_ExtensionInstanceHandle instance)](#oh_contentembed_extension_unregisteronobjectdetachfunc) | - | Unregisters the callback function for disconnecting the client OE object. You can call [OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectdetachfunc) to register the callback again.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnWriteToDataStreamFunc onWriteToDataStreamFunc)](#oh_contentembed_extension_registeronwritetodatastreamfunc) | - | Registers the callback function used when the server OE object writes data to the OE document stream.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetSnapshotFunc onGetSnapshotFunc)](#oh_contentembed_extension_registerongetsnapshotfunc) | - | Registers the callback function used when the client OE object requests to obtain the snapshot of an OE document.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnDoEditFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnDoEditFunc onDoEditFunc)](#oh_contentembed_extension_registerondoeditfunc) | - | Registers the callback function used when the client OE object requests to edit an OE document.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetEditStatusFunc onGetEditStatusFunc)](#oh_contentembed_extension_registerongeteditstatusfunc) | - | Registers the callback function used when the client OE object requests the editing state of an OE document.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetCapabilityFunc onGetCapabilityFunc)](#oh_contentembed_extension_registerongetcapabilityfunc) | - | Registers the callback function used when the client OE object queries the capabilities supported by the OE extension instance.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContentEmbedDocument(ContentEmbed_ObjectHandle object, ContentEmbed_Document **ceDocument)](#oh_contentembed_extension_getcontentembeddocument) | - | Obtains the OE document instance associated with the server OE object. The lifecycle of the document instance is managed by the system and does not need to be manually released.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnUpdate(ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_callbacktoonupdate) | - | Triggers the OE document update callback function registered with the client OE object.<br>This callback is invoked when the content of the OE document on the server changes to notify the client to refresh the document display. You are advised to call this function after the document data is modified to avoid frequently triggering the callback during the modification process.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnError(ContentEmbed_ObjectHandle object, ContentEmbed_ErrorCode code)](#oh_contentembed_extension_callbacktoonerror) | - | Triggers the OE document error callback function registered with the client OE object.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnEditingFinished(ContentEmbed_ObjectHandle object, bool dataModified)](#oh_contentembed_extension_callbacktooneditingfinished) | - | Triggers the OE document editing completion callback function registered with the client OE object.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnExtensionStopped(ContentEmbed_ExtensionInstanceHandle instance)](#oh_contentembed_extension_callbacktoonextensionstopped) | - | Triggers the OE extension stop callback function registered by all client OE objects associated with the OE extension.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_SetSnapshot(ContentEmbed_ObjectHandle object, OH_PixelmapNative *pixelMap)](#oh_contentembed_extension_setsnapshot) | - | Sets the snapshot image of the OE document associated with the client OE object.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextStartSelfUIAbility(ContentEmbed_ExtensionContextHandle context, AbilityBase_Want *want)](#oh_contentembed_extension_contextstartselfuiability) | - | Starts the [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md#uiability) through the OE extension context. To specify startup options, see [OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiabilitywithstartoptions).|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions(ContentEmbed_ExtensionContextHandle context, AbilityBase_Want *want, AbilityRuntime_StartOptions *options)](#oh_contentembed_extension_contextstartselfuiabilitywithstartoptions) | - | Starts the [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md#uiability) of the OE extension context using the startup options. If you do not need to specify startup options, see [OH_ContentEmbed_Extension_ContextStartSelfUIAbility](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiability).|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextTerminateAbility(ContentEmbed_ExtensionContextHandle context)](#oh_contentembed_extension_contextterminateability) | - | Destroys an OE extension. This function is called when an OE extension no longer needs to provide services. It destroys the extension instance through the context and releases related resources. It is recommended that this function be called after all client OE objects are disconnected and resources are cleared. After the extension is destroyed, the associated client OE objects will receive a notification indicating that the extension has stopped.|

## Function Description

### OH_ContentEmbed_Extension_GetContentEmbedContext()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContentEmbedContext(ContentEmbed_ExtensionInstanceHandle ceInstance, ContentEmbed_ExtensionContextHandle *ceContext)
```

**Description**

Obtains the OE extension context object from the OE extension instance. You can use [OH_ContentEmbed_Extension_GetContext](capi-content-embed-extension-h.md#oh_contentembed_extension_getcontext) to obtain the AbilityRuntime context, start the UIAbility using [OH_ContentEmbed_Extension_ContextStartSelfUIAbility](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiability) or [OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiabilitywithstartoptions), and destroy the OE extension using [OH_ContentEmbed_Extension_ContextTerminateAbility](capi-content-embed-extension-h.md#oh_contentembed_extension_contextterminateability).

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) ceInstance | Pointer to the OE extension instance.|
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) *ceContext |  Pointer to the context object of the OE extension instance. This is an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Extension_GetContext()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContext(ContentEmbed_ExtensionContextHandle ceContext, AbilityRuntime_ContextHandle *context)
```

**Description**

Obtains the AbilityRuntime context from the OE extension context.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) ceContext | Pointer to the OE extension context object.|
| [AbilityRuntime_ContextHandle](../apis-ability-kit/capi-abilityruntime-abilityruntime-context8h.md) *context |  Pointer to the [AbilityRuntime_ContextHandle](../apis-ability-kit/capi-abilityruntime-abilityruntime-context8h.md) context object. This is an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Extension_GetExtensionInstance()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetExtensionInstance(AbilityRuntime_ExtensionInstanceHandle baseInstance, ContentEmbed_ExtensionInstanceHandle *ceInstance)
```

**Description**

Obtains the OE extension instance from the ExtensionAbility base class instance.<br>You are advised to call this method in the [OH_AbilityRuntime_OnNativeExtensionCreate](../apis-ability-kit/capi-extension-ability-h.md#oh_abilityruntime_onnativeextensioncreate) function. After obtaining the instance, call [OH_ContentEmbed_Extension_RegisterOnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeroncreatefunc) and [OH_ContentEmbed_Extension_RegisterOnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondestroyfunc) to register the OE extension lifecycle callback functions.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [AbilityRuntime_ExtensionInstanceHandle](../apis-ability-kit/capi-abilityruntime-extensioninstance8h.md) baseInstance | Pointer to the [AbilityRuntime_ExtensionInstanceHandle](../apis-ability-kit/capi-abilityruntime-extensioninstance8h.md) base class instance.|
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) *ceInstance |  Pointer to the OE extension instance. This is an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Extension_OnCreateFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnCreateFunc)(ContentEmbed_ExtensionInstanceHandle instance, AbilityBase_Want *want)
```

**Description**

Defines the lifecycle function when the OE extension instance is created.<br>You need to implement this function and register it with the OE extension instance through [OH_ContentEmbed_Extension_RegisterOnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeroncreatefunc).

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE extension instance.|
| [AbilityBase_Want](../apis-ability-kit/capi-abilitybase-want.md) \*want | Pointer to the [AbilityBase_Want](../apis-ability-kit/capi-abilitybase-want.md) instance, which contains the startup parameters passed during OE extension creation.|

### OH_ContentEmbed_Extension_OnDestroyFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnDestroyFunc)(ContentEmbed_ExtensionInstanceHandle instance)
```

**Description**

Defines the lifecycle function when the OE extension instance is destroyed.<br>You need to implement this function and register it with the OE extension instance through [OH_ContentEmbed_Extension_RegisterOnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondestroyfunc).

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE extension instance.|

### OH_ContentEmbed_Extension_OnObjectAttachFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnObjectAttachFunc)(ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object)
```

**Description**

Defines the callback function used when the client OE object is connected to the OE extension instance. This callback function is used to perform the initialization operation after the server OE object is associated.<br>You need to implement this function and register it with the OE extension instance through [OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectattachfunc). In this callback, you need to call the [OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronwritetodatastreamfunc), [OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetcapabilityfunc), [OH_ContentEmbed_Extension_RegisterOnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondoeditfunc), [OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetsnapshotfunc), and [OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongeteditstatusfunc) functions to register the callback functions for responding to the OE object request from the client.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE extension instance.|
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|

### OH_ContentEmbed_Extension_OnObjectDetachFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnObjectDetachFunc)(ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object)
```

**Description**

Defines the callback function used when the client OE object is disconnected from the OE extension instance. This callback function is used to perform the cleanup operation after the server OE object is disconnected.<br>You need to implement this function and register it with the OE extension instance through [OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectdetachfunc).

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE extension instance.|
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|

### OH_ContentEmbed_Extension_OnWriteToDataStreamFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnWriteToDataStreamFunc)(ContentEmbed_ObjectHandle object)
```

**Description**

Defines the callback function used when the server OE object writes data to the OE document stream.<br>You need to implement this function and register it with the server OE object through [OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronwritetodatastreamfunc).

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|

### OH_ContentEmbed_Extension_OnGetSnapshotFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnGetSnapshotFunc)(ContentEmbed_ObjectHandle object)
```

**Description**

Defines the callback function used when the client OE object requests to obtain the snapshot of an OE document.<br>You need to implement this function and register it with the server OE object through [OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetsnapshotfunc).<br>In this callback, you need to call [OH_ContentEmbed_Extension_SetSnapshot](capi-content-embed-extension-h.md#oh_contentembed_extension_setsnapshot) to set the snapshot image of the OE document to respond to the client's request to obtain the snapshot.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|

### OH_ContentEmbed_Extension_OnDoEditFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnDoEditFunc)(ContentEmbed_ObjectHandle object)
```

**Description**

Defines the callback function used when the client OE object requests to edit an OE document.<br>You need to implement this function and register it with the server OE object through [OH_ContentEmbed_Extension_RegisterOnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondoeditfunc).<br>In this callback, you can start the UIAbility of your app for editing through [OH_ContentEmbed_Extension_ContextStartSelfUIAbility](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiability) and [OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiabilitywithstartoptions). After the editing is complete, you need to call [OH_ContentEmbed_Extension_CallbackToOnEditingFinished](capi-content-embed-extension-h.md#oh_contentembed_extension_callbacktooneditingfinished) to notify the client.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|

### OH_ContentEmbed_Extension_OnGetEditStatusFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnGetEditStatusFunc)(ContentEmbed_ObjectHandle object, bool *isEditing, bool *isModified)
```

**Description**

Defines the callback function used when the client OE object requests the editing state of an OE document.<br>You need to implement this function and register it with the server OE object through [OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongeteditstatusfunc).

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| bool \*isEditing |  Whether the OE document is being edited. This is an output parameter. The value **true** indicates that the document is being edited, and the value **false** indicates the opposite.|
| bool \*isModified |  Whether the OE document has been modified. This is an output parameter. The value **true** indicates that the document has been modified, and the value **false** indicates the opposite.|

### OH_ContentEmbed_Extension_OnGetCapabilityFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnGetCapabilityFunc)(ContentEmbed_ObjectHandle object, uint32_t *bitmask)
```

**Description**

Defines the callback function used when the client OE object queries the capabilities supported by the OE extension instance.<br>You need to implement this function and register it with the server OE object through [OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetcapabilityfunc).

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| uint32_t \*bitmask | Capabilities supported by the OE Extension instance. The value is a combination of values in [ContentEmbed_CapabilityCode](capi-content-embed-common-h.md#contentembed_capabilitycode).|

### OH_ContentEmbed_Extension_RegisterOnCreateFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnCreateFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnCreateFunc onCreateFunc)
```

**Description**

Registers the lifecycle function when the OE extension instance is created.<br>The callback cannot be unregistered after being registered and remains valid throughout the instance lifecycle.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE extension instance.|
| [OH_ContentEmbed_Extension_OnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_oncreatefunc) onCreateFunc | [OH_ContentEmbed_Extension_OnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_oncreatefunc) lifecycle function to register.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Extension_RegisterOnDestroyFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnDestroyFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnDestroyFunc onDestroyFunc)
```

**Description**

Registers the lifecycle function when the OE extension instance is destroyed.<br>The callback cannot be unregistered after being registered and remains valid throughout the instance lifecycle.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE extension instance.|
| [OH_ContentEmbed_Extension_OnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ondestroyfunc) onDestroyFunc | [OH_ContentEmbed_Extension_OnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ondestroyfunc) lifecycle function to be registered.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnObjectAttachFunc onObjectAttachFunc)
```

**Description**

Registers the callback function for connecting to the client OE object.<br>You can call [OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_unregisteronobjectattachfunc) to unregister the callback.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE extension instance.|
| [OH_ContentEmbed_Extension_OnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onobjectattachfunc) onObjectAttachFunc | [OH_ContentEmbed_Extension_OnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onobjectattachfunc) callback function to be registered.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc(ContentEmbed_ExtensionInstanceHandle instance)
```

**Description**

Unregisters the callback function for connecting to the client OE object. You can call [OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectattachfunc) to register the callback again.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE extension instance.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnObjectDetachFunc onObjectDetachFunc)
```

**Description**

Registers the callback function for disconnecting from the client OE object.<br>You can call [OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_unregisteronobjectdetachfunc) to unregister the callback.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE extension instance.|
| [OH_ContentEmbed_Extension_OnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onobjectdetachfunc) onObjectDetachFunc | [OH_ContentEmbed_Extension_OnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onobjectdetachfunc) callback function to be registered.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc(ContentEmbed_ExtensionInstanceHandle instance)
```

**Description**

Unregisters the callback function for disconnecting the client OE object. You can call [OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectdetachfunc) to register the callback again.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE extension instance.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnWriteToDataStreamFunc onWriteToDataStreamFunc)
```

**Description**

Registers the callback function used when the server OE object writes data to the OE document stream.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| [OH_ContentEmbed_Extension_OnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onwritetodatastreamfunc) onWriteToDataStreamFunc | [OH_ContentEmbed_Extension_OnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onwritetodatastreamfunc) callback function to be registered.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetSnapshotFunc onGetSnapshotFunc)
```

**Description**

Registers the callback function used when the client OE object requests to obtain the snapshot of an OE document.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| [OH_ContentEmbed_Extension_OnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongetsnapshotfunc) onGetSnapshotFunc | [OH_ContentEmbed_Extension_OnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongetsnapshotfunc) callback function to be registered.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Extension_RegisterOnDoEditFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnDoEditFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnDoEditFunc onDoEditFunc)
```

**Description**

Registers the callback function used when the client OE object requests to edit an OE document.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| [OH_ContentEmbed_Extension_OnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ondoeditfunc) onDoEditFunc | [OH_ContentEmbed_Extension_OnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ondoeditfunc) callback function to be registered.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetEditStatusFunc onGetEditStatusFunc)
```

**Description**

Registers the callback function used when the client OE object requests the editing state of an OE document.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| [OH_ContentEmbed_Extension_OnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongeteditstatusfunc) onGetEditStatusFunc | [OH_ContentEmbed_Extension_OnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongeteditstatusfunc) callback function to be registered.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetCapabilityFunc onGetCapabilityFunc)
```

**Description**

Registers the callback function used when the client OE object queries the capabilities supported by the OE extension instance.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| [OH_ContentEmbed_Extension_OnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongetcapabilityfunc) onGetCapabilityFunc | [OH_ContentEmbed_Extension_OnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongetcapabilityfunc) callback function to be registered.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Extension_GetContentEmbedDocument()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContentEmbedDocument(ContentEmbed_ObjectHandle object, ContentEmbed_Document **ceDocument)
```

**Description**

Obtains the OE document instance associated with the server OE object. The lifecycle of the document instance is managed by the system and does not need to be manually released.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) **ceDocument |  Pointer to the associated OE document instance. This is an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Extension_CallbackToOnUpdate()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnUpdate(ContentEmbed_ObjectHandle object)
```

**Description**

Triggers the OE document update callback function registered with the client OE object.<br>This callback is invoked when the content of the OE document on the server changes to notify the client to refresh the document display. You are advised to call this function after the document data is modified to avoid frequently triggering the callback during the modification process.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED**: The client callback is not registered.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_CLIENT_CALLBACK_FAILED**: The client callback fails to be executed.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Extension_CallbackToOnError()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnError(ContentEmbed_ObjectHandle object, ContentEmbed_ErrorCode code)
```

**Description**

Triggers the OE document error callback function registered with the client OE object.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) code | Error code. For details, see [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode).|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED**: The client callback is not registered.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_CLIENT_CALLBACK_FAILED**: The client callback fails to be executed.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Extension_CallbackToOnEditingFinished()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnEditingFinished(ContentEmbed_ObjectHandle object, bool dataModified)
```

**Description**

Triggers the OE document editing completion callback function registered with the client OE object.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| bool dataModified | Whether the document data has been modified. The value **true** indicates that the document data has been modified, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED**: The client callback is not registered.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_CLIENT_CALLBACK_FAILED**: The client callback fails to be executed.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Extension_CallbackToOnExtensionStopped()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnExtensionStopped(ContentEmbed_ExtensionInstanceHandle instance)
```

**Description**

Triggers the OE extension stop callback function registered by all client OE objects associated with the OE extension.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE extension instance.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED**: The client callback is not registered.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_CLIENT_CALLBACK_FAILED**: The client callback fails to be executed.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Extension_SetSnapshot()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_SetSnapshot(ContentEmbed_ObjectHandle object, OH_PixelmapNative *pixelMap)
```

**Description**

Sets the snapshot image of the OE document associated with the client OE object.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| [OH_PixelmapNative](../apis-arkgraphics2d/capi-drawing-oh-pixelmapnative.md) *pixelMap | Pixel map object of the document snapshot. For details, see [OH_PixelmapNative](../apis-arkgraphics2d/capi-drawing-oh-pixelmapnative.md).|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.<br>     **CE_ERR_IMAGE_PACKER_OPERATION_FAILED**: The **ImagePacker** operation fails.|

### OH_ContentEmbed_Extension_ContextStartSelfUIAbility()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextStartSelfUIAbility(ContentEmbed_ExtensionContextHandle context, AbilityBase_Want *want)
```

**Description**

Starts the [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md#uiability) through the OE extension context. To specify startup options, see [OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiabilitywithstartoptions).

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) context | Pointer to the OE extension context object.|
| [AbilityBase_Want](../apis-ability-kit/capi-abilitybase-want.md) *want | Parameters passed when the UIAbility is started. For details, see [AbilityBase_Want](../apis-ability-kit/capi-abilitybase-want.md).|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_SYSTEM_ABNORMAL**: The system service is abnormal.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions(ContentEmbed_ExtensionContextHandle context, AbilityBase_Want *want, AbilityRuntime_StartOptions *options)
```

**Description**

Starts the [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md#uiability) of the OE extension context using the startup options. If you do not need to specify startup options, see [OH_ContentEmbed_Extension_ContextStartSelfUIAbility](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiability).

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) context | Pointer to the OE extension context object.|
| [AbilityBase_Want](../apis-ability-kit/capi-abilitybase-want.md) *want | Parameters passed when the UIAbility is started. For details, see [AbilityBase_Want](../apis-ability-kit/capi-abilitybase-want.md).|
| [AbilityRuntime_StartOptions](../apis-ability-kit/capi-abilityruntime-startoptions.md) *options | Additional options for starting the UIAbility. For details, see [AbilityRuntime_StartOptions](../apis-ability-kit/capi-abilityruntime-startoptions.md).|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_SYSTEM_ABNORMAL**: The system service is abnormal.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Extension_ContextTerminateAbility()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextTerminateAbility(ContentEmbed_ExtensionContextHandle context)
```

**Description**

Destroys an OE extension. This function is called when an OE extension no longer needs to provide services. It destroys the extension instance through the context and releases related resources. It is recommended that this function be called after all client OE objects are disconnected and resources are cleared. After the extension is destroyed, the associated client OE objects will receive a notification indicating that the extension has stopped.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) context | Pointer to the OE extension context object.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_SYSTEM_ABNORMAL**: The system service is abnormal.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|
