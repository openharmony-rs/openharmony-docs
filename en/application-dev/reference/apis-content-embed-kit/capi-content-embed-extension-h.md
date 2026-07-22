# content_embed_extension.h

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1b37f75d465392a2b5313139510e8515d4fddd3d translatedAt=2026-07-17T07:41:43.999Z pushedAt=2026-07-22T11:58:09.083Z -->

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
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) | ContentEmbed_Document | Defines a struct for the OE documents, which encapsulates the metadata, content, and storage structure of the embedded document.|
| [ContentEmbed_ExtensionContext](capi-contentembed-contentembed-extensioncontext.md) | ContentEmbed_ExtensionContext | Defines a struct for the OE Extension context.|
| [ContentEmbed_ExtensionContext*](capi-contentembed-contentembed-extensioncontext8h.md) | ContentEmbed_ExtensionContextHandle | Defines the context object pointer of the OE Extension.|
| [ContentEmbed_ExtensionInstance](capi-contentembed-contentembed-extensioninstance.md) | ContentEmbed_ExtensionInstance | Defines a struct for the OE Extension instance, which manages core functions such as the lifecycle of extensions, callback registration, and association with the OE objects on the client side.|
| [ContentEmbed_ExtensionInstance*](capi-contentembed-contentembed-extensioninstance8h.md) | ContentEmbed_ExtensionInstanceHandle | Defines the object pointer of the OE Extension instance.|
| [ContentEmbed_Object](capi-contentembed-contentembed-object.md) | ContentEmbed_Object | Defines a **ContentEmbed_Object** struct, which points to the document embedding and editing object (server-side OE object) encapsulated by the OE document on the server.|
| [ContentEmbed_Object*](capi-contentembed-contentembed-object8h.md) | ContentEmbed_ObjectHandle | Defines the object pointer of **ContentEmbed_Object**.|

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContentEmbedContext(ContentEmbed_ExtensionInstanceHandle ceInstance, ContentEmbed_ExtensionContextHandle *ceContext)](#oh_contentembed_extension_getcontentembedcontext) | - | Obtains the OE Extension context object from the OE Extension instance.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContext(ContentEmbed_ExtensionContextHandle ceContext, AbilityRuntime_ContextHandle *context)](#oh_contentembed_extension_getcontext) | - | Obtains the **AbilityRuntime** context from the OE Extension context.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetExtensionInstance(AbilityRuntime_ExtensionInstanceHandle baseInstance, ContentEmbed_ExtensionInstanceHandle *ceInstance)](#oh_contentembed_extension_getextensioninstance) | - | Obtains the OE Extension instance from the **ExtensionAbility** base class instance.|
| [typedef void (\*OH_ContentEmbed_Extension_OnCreateFunc)(ContentEmbed_ExtensionInstanceHandle instance, AbilityBase_Want *want)](#oh_contentembed_extension_oncreatefunc) | OH_ContentEmbed_Extension_OnCreateFunc | This lifecycle function is triggered when an OE Extension instance is created.<br> You need to implement this function and register it with the OE Extension instance through [OH_ContentEmbed_Extension_RegisterOnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeroncreatefunc).|
| [typedef void (\*OH_ContentEmbed_Extension_OnDestroyFunc)(ContentEmbed_ExtensionInstanceHandle instance)](#oh_contentembed_extension_ondestroyfunc) | OH_ContentEmbed_Extension_OnDestroyFunc | This lifecycle function is triggered when an OE Extension instance is destroyed.<br> You need to implement this function and register it with the OE Extension instance through [OH_ContentEmbed_Extension_RegisterOnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondestroyfunc).|
| [typedef void (\*OH_ContentEmbed_Extension_OnObjectAttachFunc)(ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_onobjectattachfunc) | OH_ContentEmbed_Extension_OnObjectAttachFunc | This callback function is triggered when the client OE object is connected to the OE Extension instance. It is used to perform the initialization operation after the server OE object is associated.<br> You need to implement this function and register it with the OE Extension instance through [OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectattachfunc).|
| [typedef void (\*OH_ContentEmbed_Extension_OnObjectDetachFunc)(ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_onobjectdetachfunc) | OH_ContentEmbed_Extension_OnObjectDetachFunc | This callback function is triggered when the client OE object is disconnected from the OE Extension instance. It is used to perform the cleanup operation after the server OE object is disconnected.<br> You need to implement this function and register it with the OE Extension instance through [OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectdetachfunc).|
| [typedef void (\*OH_ContentEmbed_Extension_OnWriteToDataStreamFunc)(ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_onwritetodatastreamfunc) | OH_ContentEmbed_Extension_OnWriteToDataStreamFunc | This callback function is triggered when the server OE object writes a data stream to the OE document.<br> You need to implement this function and register it with the server OE object through [OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronwritetodatastreamfunc).|
| [typedef void (\*OH_ContentEmbed_Extension_OnGetSnapshotFunc)(ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_ongetsnapshotfunc) | OH_ContentEmbed_Extension_OnGetSnapshotFunc | This callback function is triggered when the client OE object requests to obtain the OE document snapshot.<br> You need to implement this function and register it with the server OE object through [OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetsnapshotfunc).|
| [typedef void (\*OH_ContentEmbed_Extension_OnDoEditFunc)(ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_ondoeditfunc) | OH_ContentEmbed_Extension_OnDoEditFunc | This callback function is triggered when the client OE object requests to edit the OE document.<br> You need to implement this function and register it with the server OE object through [OH_ContentEmbed_Extension_RegisterOnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondoeditfunc).|
| [typedef void (\*OH_ContentEmbed_Extension_OnGetEditStatusFunc)(ContentEmbed_ObjectHandle object, bool *isEditing, bool *isModified)](#oh_contentembed_extension_ongeteditstatusfunc) | OH_ContentEmbed_Extension_OnGetEditStatusFunc | This callback function is triggered when the client OE object requests the editing state of the OE document.<br> You need to implement this function and register it with the server-side OE object through [OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongeteditstatusfunc).|
| [typedef void (\*OH_ContentEmbed_Extension_OnGetCapabilityFunc)(ContentEmbed_ObjectHandle object, uint32_t *bitmask)](#oh_contentembed_extension_ongetcapabilityfunc) | OH_ContentEmbed_Extension_OnGetCapabilityFunc | This callback function is triggered when the client OE object queries the capabilities supported by the OE Extension instance.<br> You need to implement this function and register it with the server-side OE object through [OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetcapabilityfunc).|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnCreateFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnCreateFunc onCreateFunc)](#oh_contentembed_extension_registeroncreatefunc) | - | Registers the lifecycle function when an OE Extension instance is created.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnDestroyFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnDestroyFunc onDestroyFunc)](#oh_contentembed_extension_registerondestroyfunc) | - | Registers the lifecycle function when an OE Extension instance is destroyed.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnObjectAttachFunc onObjectAttachFunc)](#oh_contentembed_extension_registeronobjectattachfunc) | - | Registers the callback function when the client OE object is connected.<br> You can call [OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_unregisteronobjectattachfunc) to cancel the registration.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc(ContentEmbed_ExtensionInstanceHandle instance)](#oh_contentembed_extension_unregisteronobjectattachfunc) | - | Unregisters the callback function when the client OE object is connected.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnObjectDetachFunc onObjectDetachFunc)](#oh_contentembed_extension_registeronobjectdetachfunc) | - | Registers the callback function when the client OE object is disconnected.<br> You can call [OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_unregisteronobjectdetachfunc) to cancel the registration.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc(ContentEmbed_ExtensionInstanceHandle instance)](#oh_contentembed_extension_unregisteronobjectdetachfunc) | - | Unregisters the callback function when the client OE object is disconnected.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnWriteToDataStreamFunc onWriteToDataStreamFunc)](#oh_contentembed_extension_registeronwritetodatastreamfunc) | - | Registers the callback function when the server OE object writes a data stream to the OE document.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetSnapshotFunc onGetSnapshotFunc)](#oh_contentembed_extension_registerongetsnapshotfunc) | - | Registers the callback function when the client OE object requests to obtain the OE document snapshot.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnDoEditFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnDoEditFunc onDoEditFunc)](#oh_contentembed_extension_registerondoeditfunc) | - | Registers the callback function when the client OE object requests to edit an OE document.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetEditStatusFunc onGetEditStatusFunc)](#oh_contentembed_extension_registerongeteditstatusfunc) | - | Registers the callback function when the client OE object requests to obtain the editing state of an OE document.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetCapabilityFunc onGetCapabilityFunc)](#oh_contentembed_extension_registerongetcapabilityfunc) | - | Registers the callback function when the client OE object queries the capability of the OE Extension instance.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContentEmbedDocument(ContentEmbed_ObjectHandle object, ContentEmbed_Document **ceDocument)](#oh_contentembed_extension_getcontentembeddocument) | - | Obtains the OE document instance associated with the server OE object.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnUpdate(ContentEmbed_ObjectHandle object)](#oh_contentembed_extension_callbacktoonupdate) | - | This callback function is triggered when the OE document registered by the client OE object is updated.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnError(ContentEmbed_ObjectHandle object, ContentEmbed_ErrorCode code)](#oh_contentembed_extension_callbacktoonerror) | - | This callback function is triggered when an error occurs in the OE document registered by the client OE object.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnEditingFinished(ContentEmbed_ObjectHandle object, bool dataModified)](#oh_contentembed_extension_callbacktooneditingfinished) | - | This callback function is triggered when the editing of the OE document registered by the client OE object is completed.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnExtensionStopped(ContentEmbed_ExtensionInstanceHandle instance)](#oh_contentembed_extension_callbacktoonextensionstopped) | - | This callback function is triggered when the OE Extensions associated with all client OE objects stop.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_SetSnapshot(ContentEmbed_ObjectHandle object, OH_PixelmapNative *pixelMap)](#oh_contentembed_extension_setsnapshot) | - | Sets the OE document snapshot associated with the client OE object.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextStartSelfUIAbility(ContentEmbed_ExtensionContextHandle context, AbilityBase_Want *want)](#oh_contentembed_extension_contextstartselfuiability) | - | Starts the [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md#uiability) of the OE Extension using the OE Extension context.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions(ContentEmbed_ExtensionContextHandle context, AbilityBase_Want *want, AbilityRuntime_StartOptions *options)](#oh_contentembed_extension_contextstartselfuiabilitywithstartoptions) | - | Starts the [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md#uiability) of the OE Extension context using the startup option.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextTerminateAbility(ContentEmbed_ExtensionContextHandle context)](#oh_contentembed_extension_contextterminateability) | - | Destroys the OE Extension.|

## Function Description

### OH_ContentEmbed_Extension_GetContentEmbedContext()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContentEmbedContext(ContentEmbed_ExtensionInstanceHandle ceInstance, ContentEmbed_ExtensionContextHandle *ceContext)
```

**Description**

Obtains the OE Extension context object from the OE Extension instance.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) ceInstance | Pointer to the OE Extension instance.|
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) *ceContext | Output parameter. After the function is successfully called, this pointer points to the context object of the OE Extension instance.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>    **CE_ERR_NULL_POINTER**: A null pointer is returned.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: The operation is not supported in DLP sandbox applications.|

### OH_ContentEmbed_Extension_GetContext()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContext(ContentEmbed_ExtensionContextHandle ceContext, AbilityRuntime_ContextHandle *context)
```

**Description**

Obtains the **AbilityRuntime** context from the OE Extension context.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) ceContext | Pointer to the OE Extension context object.|
| [AbilityRuntime_ContextHandle](../apis-ability-kit/capi-abilityruntime-abilityruntime-context8h.md) *context | Output parameter. When the function is called successfully, this pointer points to the [AbilityRuntime_ContextHandle](../apis-ability-kit/capi-abilityruntime-abilityruntime-context8h.md) context object.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>    **CE_ERR_NULL_POINTER**: A null pointer is returned.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: The operation is not supported in DLP sandbox applications.|

### OH_ContentEmbed_Extension_GetExtensionInstance()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetExtensionInstance(AbilityRuntime_ExtensionInstanceHandle baseInstance, ContentEmbed_ExtensionInstanceHandle *ceInstance)
```

**Description**

Obtains the OE Extension instance from the **ExtensionAbility** base class instance.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_ExtensionInstanceHandle](../apis-ability-kit/capi-abilityruntime-extensioninstance8h.md) baseInstance | [AbilityRuntime_ExtensionInstanceHandle](../apis-ability-kit/capi-abilityruntime-extensioninstance8h.md) instance.|
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) *ceInstance | Output parameter. When the function is called successfully, this pointer points to the OE Extension instance.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>    **CE_ERR_NULL_POINTER**: A null pointer is returned.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: The operation is not supported in DLP sandbox applications.|

### OH_ContentEmbed_Extension_OnCreateFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnCreateFunc)(ContentEmbed_ExtensionInstanceHandle instance, AbilityBase_Want *want)
```

**Description**

This lifecycle function is triggered when an OE Extension instance is created.<br> You need to implement this function and register it with the OE Extension instance through [OH_ContentEmbed_Extension_RegisterOnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeroncreatefunc).

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance.|
| [AbilityBase_Want](../apis-ability-kit/capi-abilitybase-want.md) \*want | Pointer to the [AbilityBase_Want](../apis-ability-kit/capi-abilitybase-want.md) instance.|

### OH_ContentEmbed_Extension_OnDestroyFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnDestroyFunc)(ContentEmbed_ExtensionInstanceHandle instance)
```

**Description**

This lifecycle function is triggered when an OE Extension instance is destroyed.<br> You need to implement this function and register it with the OE Extension instance through [OH_ContentEmbed_Extension_RegisterOnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondestroyfunc).

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance.|

### OH_ContentEmbed_Extension_OnObjectAttachFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnObjectAttachFunc)(ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object)
```

**Description**

This callback function is triggered when the client OE object is connected to the OE Extension instance. It is used to perform the initialization operation after the server OE object is associated.<br> You need to implement this function and register it with the OE Extension instance through [OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectattachfunc).

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance.|
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|

### OH_ContentEmbed_Extension_OnObjectDetachFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnObjectDetachFunc)(ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object)
```

**Description**

This callback function is triggered when the client OE object is disconnected from the OE Extension instance. It is used to perform the cleanup operation after the server OE object is disconnected.<br> You need to implement this function and register it with the OE Extension instance through [OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectdetachfunc).

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance.|
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|

### OH_ContentEmbed_Extension_OnWriteToDataStreamFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnWriteToDataStreamFunc)(ContentEmbed_ObjectHandle object)
```

**Description**

This callback function is triggered when the server OE object writes a data stream to the OE document.<br> You need to implement this function and register it with the server OE object through [OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronwritetodatastreamfunc).

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|

### OH_ContentEmbed_Extension_OnGetSnapshotFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnGetSnapshotFunc)(ContentEmbed_ObjectHandle object)
```

**Description**

This callback function is triggered when the client OE object requests to obtain the OE document snapshot.<br> You need to implement this function and register it with the server OE object through [OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetsnapshotfunc).

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|

### OH_ContentEmbed_Extension_OnDoEditFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnDoEditFunc)(ContentEmbed_ObjectHandle object)
```

**Description**

This callback function is triggered when the client OE object requests to edit the OE document.<br> You need to implement this function and register it with the server OE object through [OH_ContentEmbed_Extension_RegisterOnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerondoeditfunc).

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|

### OH_ContentEmbed_Extension_OnGetEditStatusFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnGetEditStatusFunc)(ContentEmbed_ObjectHandle object, bool *isEditing, bool *isModified)
```

**Description**

This callback function is triggered when the client OE object requests the editing state of the OE document.<br> You need to implement this function and register it with the server-side OE object through [OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongeteditstatusfunc).

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| bool \*isEditing | Output parameter, which indicates whether the OE document is being edited. The value **true** indicates that the document is being edited, and the value **false** indicates otherwise.|
| bool \*isModified | Output parameter, which indicates whether the OE document has been modified. The value **true** indicates that the document has been modified, and the value **false** indicates otherwise.|

### OH_ContentEmbed_Extension_OnGetCapabilityFunc()

```c
typedef void (*OH_ContentEmbed_Extension_OnGetCapabilityFunc)(ContentEmbed_ObjectHandle object, uint32_t *bitmask)
```

**Description**

This callback function is triggered when the client OE object queries the capabilities supported by the OE Extension instance.<br> You need to implement this function and register it with the server-side OE object through [OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registerongetcapabilityfunc).

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| uint32_t \*bitmask | Output parameter, which indicates the capabilities supported by the OE Extension instance. This parameter combines the values in [ContentEmbed_CapabilityCode](capi-content-embed-common-h.md#contentembed_capabilitycode).|

### OH_ContentEmbed_Extension_RegisterOnCreateFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnCreateFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnCreateFunc onCreateFunc)
```

**Description**

Registers the lifecycle function when an OE Extension instance is created.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance.|
| [OH_ContentEmbed_Extension_OnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_oncreatefunc) onCreateFunc | [OH_ContentEmbed_Extension_OnCreateFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_oncreatefunc) to register.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: The operation is not supported in DLP sandbox applications.|

### OH_ContentEmbed_Extension_RegisterOnDestroyFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnDestroyFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnDestroyFunc onDestroyFunc)
```

**Description**

Registers the lifecycle function when an OE Extension instance is destroyed.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance.|
| [OH_ContentEmbed_Extension_OnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ondestroyfunc) onDestroyFunc | [OH_ContentEmbed_Extension_OnDestroyFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ondestroyfunc) to register.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: The operation is not supported in DLP sandbox applications.|

### OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnObjectAttachFunc onObjectAttachFunc)
```

**Description**

Registers the callback function when the client OE object is connected.<br> You can call [OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_unregisteronobjectattachfunc) to cancel the registration.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance.|
| [OH_ContentEmbed_Extension_OnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onobjectattachfunc) onObjectAttachFunc | [OH_ContentEmbed_Extension_OnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onobjectattachfunc) to register.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: The operation is not supported in DLP sandbox applications.|

### OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_UnRegisterOnObjectAttachFunc(ContentEmbed_ExtensionInstanceHandle instance)
```

**Description**

Unregisters the callback function when the client OE object is connected.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: The operation is not supported in DLP sandbox applications.|

### OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc(ContentEmbed_ExtensionInstanceHandle instance, OH_ContentEmbed_Extension_OnObjectDetachFunc onObjectDetachFunc)
```

**Description**

Registers the callback function when the client OE object is disconnected.<br> You can call [OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_unregisteronobjectdetachfunc) to cancel the registration.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the instance object of the OpenHarmony Extension.|
| [OH_ContentEmbed_Extension_OnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onobjectdetachfunc) onObjectDetachFunc | [OH_ContentEmbed_Extension_OnObjectDetachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onobjectdetachfunc) to register.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: The operation is not supported in DLP sandbox applications.|

### OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_UnRegisterOnObjectDetachFunc(ContentEmbed_ExtensionInstanceHandle instance)
```

**Description**

Unregisters the callback function when the client OE object is disconnected.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: The operation is not supported in DLP sandbox applications.|

### OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnWriteToDataStreamFunc onWriteToDataStreamFunc)
```

**Description**

Registers the callback function when the server OE object writes a data stream to the OE document.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| [OH_ContentEmbed_Extension_OnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onwritetodatastreamfunc) onWriteToDataStreamFunc | [OH_ContentEmbed_Extension_OnWriteToDataStreamFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onwritetodatastreamfunc) to register.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: The operation is not supported in DLP sandbox applications.|

### OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetSnapshotFunc onGetSnapshotFunc)
```

**Description**

Registers the callback function when the client OE object requests to obtain the OE document snapshot.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| [OH_ContentEmbed_Extension_OnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongetsnapshotfunc) onGetSnapshotFunc | [OH_ContentEmbed_Extension_OnGetSnapshotFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongetsnapshotfunc) to register.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: The operation is not supported in DLP sandbox applications.|

### OH_ContentEmbed_Extension_RegisterOnDoEditFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnDoEditFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnDoEditFunc onDoEditFunc)
```

**Description**

Registers the callback function when the client OE object requests to edit an OE document.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| [OH_ContentEmbed_Extension_OnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ondoeditfunc) onDoEditFunc | [OH_ContentEmbed_Extension_OnDoEditFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ondoeditfunc) to register.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: The operation is not supported in DLP sandbox applications.|

### OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetEditStatusFunc onGetEditStatusFunc)
```

**Description**

Registers the callback function when the client OE object requests to obtain the editing state of an OE document.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| [OH_ContentEmbed_Extension_OnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongeteditstatusfunc) onGetEditStatusFunc | [OH_ContentEmbed_Extension_OnGetEditStatusFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongeteditstatusfunc) to register.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: The operation is not supported in DLP sandbox applications.|

### OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc(ContentEmbed_ObjectHandle object, OH_ContentEmbed_Extension_OnGetCapabilityFunc onGetCapabilityFunc)
```

**Description**

Registers the callback function when the client OE object queries the capability of the OE Extension instance.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| [OH_ContentEmbed_Extension_OnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongetcapabilityfunc) onGetCapabilityFunc | [OH_ContentEmbed_Extension_OnGetCapabilityFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_ongetcapabilityfunc) to register.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: The operation is not supported in DLP sandbox applications.|

### OH_ContentEmbed_Extension_GetContentEmbedDocument()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_GetContentEmbedDocument(ContentEmbed_ObjectHandle object, ContentEmbed_Document **ceDocument)
```

**Description**

Obtains the OE document instance associated with the server OE object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) **ceDocument | Output parameter. When the function is called successfully, this pointer points to the associated OE document instance.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>    **CE_ERR_NULL_POINTER**: A null pointer is returned.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: The operation is not supported in DLP sandbox applications.|

### OH_ContentEmbed_Extension_CallbackToOnUpdate()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnUpdate(ContentEmbed_ObjectHandle object)
```

**Description**

This callback function is triggered when the OE document registered by the client OE object is updated.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: A null pointer is returned.<br>     **CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED**: The client callback is not registered.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The operation is not supported on the device.<br>     **CE_ERR_CLIENT_CALLBACK_FAILED**: The client callback fails to be executed.<br>     **CE_ERR_IN_DLP_SANDBOX**: The operation is not supported in DLP sandbox applications.|

### OH_ContentEmbed_Extension_CallbackToOnError()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnError(ContentEmbed_ObjectHandle object, ContentEmbed_ErrorCode code)
```

**Description**

This callback function is triggered when an error occurs in the OE document registered by the client OE object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) code | Error code. For details, see [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode).|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: A null pointer is returned.<br>     **CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED**: The client callback is not registered.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The operation is not supported on the device.<br>     **CE_ERR_CLIENT_CALLBACK_FAILED**: The client callback fails to be executed.<br>     **CE_ERR_IN_DLP_SANDBOX**: The operation is not supported in DLP sandbox applications.|

### OH_ContentEmbed_Extension_CallbackToOnEditingFinished()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnEditingFinished(ContentEmbed_ObjectHandle object, bool dataModified)
```

**Description**

This callback function is triggered when the editing of the OE document registered by the client OE object is completed.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| bool dataModified | Whether data in the document has been modified. The value **true** indicates that the data has been modified, and the value **false** indicates otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: A null pointer is returned.<br>     **CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED**: The client callback is not registered.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The operation is not supported on the device.<br>     **CE_ERR_CLIENT_CALLBACK_FAILED**: The client callback fails to be executed.<br>     **CE_ERR_IN_DLP_SANDBOX**: The operation is not supported in DLP sandbox applications.|

### OH_ContentEmbed_Extension_CallbackToOnExtensionStopped()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_CallbackToOnExtensionStopped(ContentEmbed_ExtensionInstanceHandle instance)
```

**Description**

This callback function is triggered when the OE Extensions associated with all client OE objects stop.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionInstanceHandle](capi-contentembed-contentembed-extensioninstance8h.md) instance | Pointer to the OE Extension instance.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: A null pointer is returned.<br>     **CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED**: The client callback is not registered.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The operation is not supported on the device.<br>     **CE_ERR_CLIENT_CALLBACK_FAILED**: The client callback fails to be executed.<br>     **CE_ERR_IN_DLP_SANDBOX**: The operation is not supported in DLP sandbox applications.|

### OH_ContentEmbed_Extension_SetSnapshot()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_SetSnapshot(ContentEmbed_ObjectHandle object, OH_PixelmapNative *pixelMap)
```

**Description**

Sets the snapshot image of the OE document associated with the client-side OE object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) object | [ContentEmbed_ObjectHandle](capi-contentembed-contentembed-object8h.md) instance.|
| [OH_PixelmapNative](../apis-arkgraphics2d/capi-drawing-oh-pixelmapnative.md) *pixelMap | Pixel map object of the document snapshot. For details, see [OH_PixelmapNative](../apis-arkgraphics2d/capi-drawing-oh-pixelmapnative.md).|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: A null pointer is returned.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: The operation is not supported in DLP sandbox applications.<br>     **CE_ERR_IMAGE_PACKER_OPERATION_FAILED**: The image operation fails.|

### OH_ContentEmbed_Extension_ContextStartSelfUIAbility()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextStartSelfUIAbility(ContentEmbed_ExtensionContextHandle context, AbilityBase_Want *want)
```

**Description**

Starts the [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md#uiability) of the OE Extension using the OE Extension context.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) context | Pointer to the OE Extension context object.|
| [AbilityBase_Want](../apis-ability-kit/capi-abilitybase-want.md) *want | Parameter passed when the UIAbility is started. For details, see [AbilityBase_Want](../apis-ability-kit/capi-abilitybase-want.md).|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: A null pointer is returned.<br>     **CE_ERR_SYSTEM_ABNORMAL**: The system service is abnormal.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: The operation is not supported in DLP sandbox applications.|

### OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions(ContentEmbed_ExtensionContextHandle context, AbilityBase_Want *want, AbilityRuntime_StartOptions *options)
```

**Description**

Starts the [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md#uiability) of the OE Extension context using the startup option.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) context | Pointer to the OE Extension context object.|
| [AbilityBase_Want](../apis-ability-kit/capi-abilitybase-want.md) *want | Parameter passed when the UIAbility is started. For details, see [AbilityBase_Want](../apis-ability-kit/capi-abilitybase-want.md).|
| [AbilityRuntime_StartOptions](../apis-ability-kit/capi-abilityruntime-startoptions.md) *options | Additional options for starting the UIAbility. For details, see [AbilityRuntime_StartOptions](../apis-ability-kit/capi-abilityruntime-startoptions.md).|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: A null pointer is returned.<br>     **CE_ERR_SYSTEM_ABNORMAL**: The system service is abnormal.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: The operation is not supported in DLP sandbox applications.|

### OH_ContentEmbed_Extension_ContextTerminateAbility()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Extension_ContextTerminateAbility(ContentEmbed_ExtensionContextHandle context)
```

**Description**

Destroys the OE Extension.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionContextHandle](capi-contentembed-contentembed-extensioncontext8h.md) context | Pointer to the OE Extension context object.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: A null pointer is returned.<br>     **CE_ERR_SYSTEM_ABNORMAL**: The system service is abnormal.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: The operation is not supported in DLP sandbox applications.|