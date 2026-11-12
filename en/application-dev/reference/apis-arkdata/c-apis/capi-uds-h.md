# uds.h

## Overview

Defines the APIs and structs related to the uniform data structs. If the parameter type is char*, the string must end with a null character ('\0').

**Library**: libudmf.so

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Related module**: [UDMF](capi-arkdata-udmf.md)

## Summary

### Structs

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_UDMF_VirtualFileCallbacks](capi-udmf-oh-udmf-virtualfilecallbacks.md) | OH_UDMF_VirtualFileCallbacks | Describes the callbacks used to provide virtual file metadata and content.<br> <code>structSize</code> must be set to <code>sizeof(OH_UDMF_VirtualFileCallbacks)</code>. <code>onRead</code> is mandatory, and <code>onStat</code> and <code>onCancel</code> are optional. All files must be pre-declared in size. Set <code>onCancel</code> to nullptr if you do not need to cancel the notification. Different threads may invoke callbacks concurrently. Callbacks cannot be blocked indefinitely. |
| [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md) | OH_UdsPlainText | Describes the unified data struct of plaintext. |
| [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md) | OH_UdsHyperlink | Describes the unified data struct of hyperlink. |
| [OH_UdsHtml](capi-udmf-oh-udshtml.md) | OH_UdsHtml | Defines a struct for the unified data of the Hypertext Markup Language (HTML) type. |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md) | OH_UdsAppItem | Describes the unified data struct of open harmony application item. |
| [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md) | OH_UdsFileUri | Describes the unified data struct of file uri. |
| [OH_UDMF_VirtualItem](capi-udmf-oh-udmf-virtualitem.md) | OH_UDMF_VirtualItem | Describes a virtual file or virtual directory node. |
| [OH_UDMF_VirtualFileInfo](capi-udmf-oh-udmf-virtualfileinfo.md) | OH_UDMF_VirtualFileInfo | Describes virtual file entries and their data callbacks. |
| [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md) | OH_UdsPixelMap | Describes the unified data struct of open harmony pixel map. |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md) | OH_UdsContentForm | Defines a struct for the unified data of the content card type. |
| [OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md) | OH_UdsArrayBuffer | Describes the unified data struct of array buffer. |
| [OH_UdsDetails](capi-udmf-oh-udsdetails.md) | OH_UdsDetails | Describes the key-value object of UDS data. |

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Udmf_AuthPermission](#udmf_authpermission) | Udmf_AuthPermission | Enumerates the URI authorization policies in the drag scenario.<br> > **NOTE**<br>> > This authorization policy takes effect only in drag scenarios.<br> The **NONE**, **READ**, **WRITE**, and **PERSIST** policies are supported. They can be combined, and only the following combinations take effect:<br> - **NONE**: No file permission is granted. - **READ**: Only one-time read permission is granted. - **WRITE**: Only one-time read and write permissions are granted. (Write permission includes read permission.) - **READ+WRITE**: One-time read and write authorization is performed, which is equivalent to **WRITE** authorization. - **READ+PERSIST**: Persistent read permission is granted. - **WRITE+PERSIST**: Persistent read and write permissions are granted. - **READ+WRITE+PERSIST**: Persistent read and write permissions are granted. The rules for applying the drag authorization policies are as follows (in descending order of priority): - Single data level: The **FileUri** and **HTML** (UDSs) support the configuration of authorization policy parameters, which take effect only once for a single record and have the highest priority. - [OH_UdmfData](capi-udmf-oh-udmfdata.md) level: The authorization parameters provided in [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md) are valid for a single drag operation. If an authorization policy is configured for a piece of data, the configuration of the data is preferentially used. This level has the second highest priority. - Default level: If no authorization policy is configured for a single piece of data or [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md), proxy authorization is performed based on the default drag logic. The default logic is as follows: - FileUri data: By default, the **READ**, **WRITE**, and **PERSIST** permissions are granted in drag scenarios. - HTML data: Grants read permission only to the URIs in the img tags of the HTML text. |

### Functions

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef OH_UDMF_VirtualItem* (\*OH_UDMF_VirtualFileOnStat)(void* context, const char* id)](#oh_udmf_virtualfileonstat) | OH_UDMF_VirtualFileOnStat | This interface is invoked when virtual file metadata needs to be obtained.<br> The returned node must be created by [OH_UDMF_CreateVirtualFileItem](capi-uds-h.md#oh_udmf_createvirtualfileitem), its ownership is transferred to UDMF, and the node cannot be destroyed after the callback returns. |
| [typedef int (\*OH_UDMF_VirtualFileOnRead)(void* context, const char* id, int64_t offset, uint32_t length, uint8_t* data, uint32_t* bytesRead)](#oh_udmf_virtualfileonread) | OH_UDMF_VirtualFileOnRead | This function is invoked when virtual file data needs to be read.<br> A maximum of <code>length</code> bytes can be written to <code>data</code> and the actual number of written bytes can be returned through <code>bytesRead</code>. The actual number of bytes can be less than <code>length</code> or zero. |
| [typedef int (\*OH_UDMF_VirtualFileOnCancel)(void* context, const char* const *idList, uint32_t count)](#oh_udmf_virtualfileoncancel) | OH_UDMF_VirtualFileOnCancel | Called when a virtual file operation is canceled. |
| [typedef void (\*OH_UDMF_VirtualFileFinalize)(void* context)](#oh_udmf_virtualfilefinalize) | OH_UDMF_VirtualFileFinalize | Releases the user contexts held by the UDMF.<br> This callback is executed only once after all virtual file objects referencing the context are freed. The callback may be executed on any thread. |
| [OH_UdsPlainText* OH_UdsPlainText_Create()](#oh_udsplaintext_create) | - | Creates an [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md) instance and a pointer to it. If this pointer is no longer required, use {@lOH_UdsPlainText_Destroy} to destroy it. Otherwise, memory leaks may occur. |
| [void OH_UdsPlainText_Destroy(OH_UdsPlainText* pThis)](#oh_udsplaintext_destroy) | - | Destroy a pointer that points to the [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md) instance. |
| [const char* OH_UdsPlainText_GetType(OH_UdsPlainText* pThis)](#oh_udsplaintext_gettype) | - | Get type id from the [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md). |
| [const char* OH_UdsPlainText_GetContent(OH_UdsPlainText* pThis)](#oh_udsplaintext_getcontent) | - | Get content from the [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md). |
| [const char* OH_UdsPlainText_GetAbstract(OH_UdsPlainText* pThis)](#oh_udsplaintext_getabstract) | - | Get abstract from the [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md). |
| [int OH_UdsPlainText_GetDetails(OH_UdsPlainText* pThis, OH_UdsDetails* details)](#oh_udsplaintext_getdetails) | - | Get details from the [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md). |
| [int OH_UdsPlainText_SetContent(OH_UdsPlainText* pThis, const char* content)](#oh_udsplaintext_setcontent) | - | Set content to the [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md). |
| [int OH_UdsPlainText_SetAbstract(OH_UdsPlainText* pThis, const char* abstract)](#oh_udsplaintext_setabstract) | - | Set abstract to the [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md). |
| [int OH_UdsPlainText_SetDetails(OH_UdsPlainText* pThis, const OH_UdsDetails* details)](#oh_udsplaintext_setdetails) | - | Set details to the [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md). |
| [OH_UdsHyperlink* OH_UdsHyperlink_Create()](#oh_udshyperlink_create) | - | Creates a pointer to the instance of the [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md). |
| [void OH_UdsHyperlink_Destroy(OH_UdsHyperlink* pThis)](#oh_udshyperlink_destroy) | - | Destroy a pointer that points to the [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md) instance. |
| [const char* OH_UdsHyperlink_GetType(OH_UdsHyperlink* pThis)](#oh_udshyperlink_gettype) | - | Obtains the type ID from an [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md) instance. |
| [const char* OH_UdsHyperlink_GetUrl(OH_UdsHyperlink* pThis)](#oh_udshyperlink_geturl) | - | Get url from the [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md). |
| [const char* OH_UdsHyperlink_GetDescription(OH_UdsHyperlink* pThis)](#oh_udshyperlink_getdescription) | - | Get description from the [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md). |
| [int OH_UdsHyperlink_GetDetails(OH_UdsHyperlink* pThis, OH_UdsDetails* details)](#oh_udshyperlink_getdetails) | - | Get details from the [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md). |
| [int OH_UdsHyperlink_SetUrl(OH_UdsHyperlink* pThis, const char* url)](#oh_udshyperlink_seturl) | - | Set url to the [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md). |
| [int OH_UdsHyperlink_SetDescription(OH_UdsHyperlink* pThis, const char* description)](#oh_udshyperlink_setdescription) | - | Set description to the [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md). |
| [int OH_UdsHyperlink_SetDetails(OH_UdsHyperlink* pThis, const OH_UdsDetails* details)](#oh_udshyperlink_setdetails) | - | Set details to the [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md). |
| [OH_UdsHtml* OH_UdsHtml_Create()](#oh_udshtml_create) | - | Creates a pointer to the instance of the [OH_UdsHtml](capi-udmf-oh-udshtml.md). |
| [void OH_UdsHtml_Destroy(OH_UdsHtml* pThis)](#oh_udshtml_destroy) | - | Destroy a pointer that points to the [OH_UdsHtml](capi-udmf-oh-udshtml.md) instance. |
| [const char* OH_UdsHtml_GetType(OH_UdsHtml* pThis)](#oh_udshtml_gettype) | - | Obtains the type ID from an [OH_UdsHtml](capi-udmf-oh-udshtml.md) instance. |
| [const char* OH_UdsHtml_GetContent(OH_UdsHtml* pThis)](#oh_udshtml_getcontent) | - | Get content from the [OH_UdsHtml](capi-udmf-oh-udshtml.md). |
| [const char* OH_UdsHtml_GetPlainContent(OH_UdsHtml* pThis)](#oh_udshtml_getplaincontent) | - | Get plain content from the [OH_UdsHtml](capi-udmf-oh-udshtml.md). |
| [int OH_UdsHtml_GetDetails(OH_UdsHtml* pThis, OH_UdsDetails* details)](#oh_udshtml_getdetails) | - | Get details from the [OH_UdsHtml](capi-udmf-oh-udshtml.md). |
| [int OH_UdsHtml_SetContent(OH_UdsHtml* pThis, const char* content)](#oh_udshtml_setcontent) | - | Set content to the [OH_UdsHtml](capi-udmf-oh-udshtml.md). |
| [int OH_UdsHtml_SetPlainContent(OH_UdsHtml* pThis, const char* plainContent)](#oh_udshtml_setplaincontent) | - | Set plain content to the [OH_UdsHtml](capi-udmf-oh-udshtml.md). |
| [int OH_UdsHtml_SetDetails(OH_UdsHtml* pThis, const OH_UdsDetails* details)](#oh_udshtml_setdetails) | - | Set details to the [OH_UdsHtml](capi-udmf-oh-udshtml.md). |
| [int OH_UdsHtml_SetAuthPolicy(OH_UdsHtml* pThis, uint32_t authPolicy)](#oh_udshtml_setauthpolicy) | - | Set the authorization policy to [OH_UdsHtml](capi-udmf-oh-udshtml.md). |
| [OH_UdsAppItem* OH_UdsAppItem_Create()](#oh_udsappitem_create) | - | Creates a pointer to the instance of the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |
| [void OH_UdsAppItem_Destroy(OH_UdsAppItem* pThis)](#oh_udsappitem_destroy) | - | Destroy a pointer that points to the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md) instance. |
| [const char* OH_UdsAppItem_GetType(OH_UdsAppItem* pThis)](#oh_udsappitem_gettype) | - | Get type from the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |
| [const char* OH_UdsAppItem_GetId(OH_UdsAppItem* pThis)](#oh_udsappitem_getid) | - | Get app id from the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |
| [const char* OH_UdsAppItem_GetName(OH_UdsAppItem* pThis)](#oh_udsappitem_getname) | - | Get app name from the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |
| [const char* OH_UdsAppItem_GetIconId(OH_UdsAppItem* pThis)](#oh_udsappitem_geticonid) | - | Get app icon id from the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |
| [const char* OH_UdsAppItem_GetLabelId(OH_UdsAppItem* pThis)](#oh_udsappitem_getlabelid) | - | Get app label id from the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |
| [const char* OH_UdsAppItem_GetBundleName(OH_UdsAppItem* pThis)](#oh_udsappitem_getbundlename) | - | Get bundle name from the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |
| [const char* OH_UdsAppItem_GetAbilityName(OH_UdsAppItem* pThis)](#oh_udsappitem_getabilityname) | - | Get ability name from the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |
| [int OH_UdsAppItem_GetDetails(OH_UdsAppItem* pThis, OH_UdsDetails* details)](#oh_udsappitem_getdetails) | - | Get details from the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |
| [int OH_UdsAppItem_SetId(OH_UdsAppItem* pThis, const char* appId)](#oh_udsappitem_setid) | - | Set application id to the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |
| [int OH_UdsAppItem_SetName(OH_UdsAppItem* pThis, const char* appName)](#oh_udsappitem_setname) | - | Set application name to the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |
| [int OH_UdsAppItem_SetIconId(OH_UdsAppItem* pThis, const char* appIconId)](#oh_udsappitem_seticonid) | - | Set application icon id to the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |
| [int OH_UdsAppItem_SetLabelId(OH_UdsAppItem* pThis, const char* appLabelId)](#oh_udsappitem_setlabelid) | - | Set application label id to the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |
| [int OH_UdsAppItem_SetBundleName(OH_UdsAppItem* pThis, const char* bundleName)](#oh_udsappitem_setbundlename) | - | Set bundle name to the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |
| [int OH_UdsAppItem_SetAbilityName(OH_UdsAppItem* pThis, const char* abilityName)](#oh_udsappitem_setabilityname) | - | Set ability name to the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |
| [int OH_UdsAppItem_SetDetails(OH_UdsAppItem* pThis, const OH_UdsDetails* details)](#oh_udsappitem_setdetails) | - | Set details to the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |
| [OH_UdsFileUri* OH_UdsFileUri_Create()](#oh_udsfileuri_create) | - | Creates a pointer to the instance of the [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md). |
| [void OH_UdsFileUri_Destroy(OH_UdsFileUri* pThis)](#oh_udsfileuri_destroy) | - | Destroy a pointer that points to the [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md) instance. |
| [const char* OH_UdsFileUri_GetType(OH_UdsFileUri* pThis)](#oh_udsfileuri_gettype) | - | Get type id from the [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md). |
| [const char* OH_UdsFileUri_GetFileUri(OH_UdsFileUri* pThis)](#oh_udsfileuri_getfileuri) | - | Get file uri from the [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md). |
| [const char* OH_UdsFileUri_GetFileType(OH_UdsFileUri* pThis)](#oh_udsfileuri_getfiletype) | - | Get file type from the [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md). |
| [int OH_UdsFileUri_GetDetails(OH_UdsFileUri* pThis, OH_UdsDetails* details)](#oh_udsfileuri_getdetails) | - | Get details from the [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md). |
| [int OH_UdsFileUri_SetFileUri(OH_UdsFileUri* pThis, const char* fileUri)](#oh_udsfileuri_setfileuri) | - | Set file uri to the [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md). |
| [int OH_UdsFileUri_SetFileType(OH_UdsFileUri* pThis, const char* fileType)](#oh_udsfileuri_setfiletype) | - | Set file type to the [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md). |
| [int OH_UdsFileUri_SetDetails(OH_UdsFileUri* pThis, const OH_UdsDetails* details)](#oh_udsfileuri_setdetails) | - | Set details to the [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md). |
| [int OH_UdsFileUri_SetAuthPolicy(OH_UdsFileUri* pThis, uint32_t authPolicy)](#oh_udsfileuri_setauthpolicy) | - | Set the authorization policy to [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md). |
| [OH_UDMF_VirtualItem* OH_UDMF_CreateVirtualFileItem(const char* name, const char* id, int64_t modifyTime)](#oh_udmf_createvirtualfileitem) | - | Create a virtual file node that must explicitly set the file size.<br> Before adding a node to a directory or creating virtual file information, you must call [OH_UDMF_SetVirtualFileSize](capi-uds-h.md#oh_udmf_setvirtualfilesize) to set the file size. A size of zero indicates an empty file, and the file size will not be inferred by other means when the size is not set. |
| [OH_UDMF_VirtualItem* OH_UDMF_CreateVirtualDirectoryItem(const char* name, int64_t modifyTime)](#oh_udmf_createvirtualdirectoryitem) | - | Create a virtual directory node. |
| [void OH_UDMF_DestroyVirtualItem(OH_UDMF_VirtualItem* item)](#oh_udmf_destroyvirtualitem) | - | Destroy a virtual node. |
| [int OH_UDMF_SetVirtualFileSize(OH_UDMF_VirtualItem* item, int64_t size)](#oh_udmf_setvirtualfilesize) | - | Set the file size of a virtual file node. |
| [int OH_UDMF_ClearVirtualFileSize(OH_UDMF_VirtualItem* item)](#oh_udmf_clearvirtualfilesize) | - | The file size that must be set for the virtual file node is cleared during the build process.<br> After clearing, the non-negative file size must be set again via [OH_UDMF_SetVirtualFileSize](capi-uds-h.md#oh_udmf_setvirtualfilesize) before the node can be added to the directory or used to create Virtual file information; The stat callback cannot replace this step. |
| [int OH_UDMF_AddVirtualItemChild(OH_UDMF_VirtualItem* directory, const OH_UDMF_VirtualItem* child)](#oh_udmf_addvirtualitemchild) | - | Adds a child node to the virtual directory.<br> This interface copies <code>child</code>, and the caller still retains the ownership of the original node. |
| [OH_UDMF_VirtualFileInfo* OH_UDMF_CreateVirtualFileInfo(const OH_UDMF_VirtualItem* itemInfo, const OH_UDMF_VirtualFileCallbacks* callbacks, void* context, OH_UDMF_VirtualFileFinalize finalize)](#oh_udmf_createvirtualfileinfo) | - | Create virtual file information.<br> This interface copies the node tree and callback table. <code>finalize</code> must be provided when <code>context</code> is not nullptr. After the interface is successfully executed, the UDMF holds the context until the last reference is released. |
| [void OH_UDMF_DestroyVirtualFileInfo(OH_UDMF_VirtualFileInfo* info)](#oh_udmf_destroyvirtualfileinfo) | - | Destroy virtual file information.<br> When virtual file information has been attached to a file URI or unified data record, the callback state remains in effect until all related references are released. |
| [int OH_UDMF_SetFileUriVirtualEntry(OH_UdsFileUri* fileUri, const OH_UDMF_VirtualFileInfo* info)](#oh_udmf_setfileurivirtualentry) | - | Appends virtual file information to the file URI. |
| [int OH_UDMF_ClearFileUriVirtualEntry(OH_UdsFileUri* fileUri)](#oh_udmf_clearfileurivirtualentry) | - | Removes virtual file information from file URI. |
| [OH_UdsPixelMap* OH_UdsPixelMap_Create()](#oh_udspixelmap_create) | - | Creates a pointer to the instance of the [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md). |
| [void OH_UdsPixelMap_Destroy(OH_UdsPixelMap* pThis)](#oh_udspixelmap_destroy) | - | Destroy a pointer that points to the [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md) instance. |
| [const char* OH_UdsPixelMap_GetType(OH_UdsPixelMap* pThis)](#oh_udspixelmap_gettype) | - | Get type id from the [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md). |
| [void OH_UdsPixelMap_GetPixelMap(OH_UdsPixelMap* pThis, OH_PixelmapNative* pixelmapNative)](#oh_udspixelmap_getpixelmap) | - | Get pixel map from the [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md). |
| [int OH_UdsPixelMap_GetDetails(OH_UdsPixelMap* pThis, OH_UdsDetails* details)](#oh_udspixelmap_getdetails) | - | Get details from the [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md). |
| [int OH_UdsPixelMap_SetPixelMap(OH_UdsPixelMap* pThis, OH_PixelmapNative* pixelmapNative)](#oh_udspixelmap_setpixelmap) | - | Set pixel map to the [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md). |
| [int OH_UdsPixelMap_SetDetails(OH_UdsPixelMap* pThis, const OH_UdsDetails* details)](#oh_udspixelmap_setdetails) | - | Set details to the [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md). |
| [OH_UdsArrayBuffer* OH_UdsArrayBuffer_Create()](#oh_udsarraybuffer_create) | - | Creates a pointer to the instance of the [OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md). |
| [int OH_UdsArrayBuffer_Destroy(OH_UdsArrayBuffer* buffer)](#oh_udsarraybuffer_destroy) | - | Destroy a pointer that points to the [OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md) instance. |
| [int OH_UdsArrayBuffer_SetData(OH_UdsArrayBuffer* buffer, unsigned char* data, unsigned int len)](#oh_udsarraybuffer_setdata) | - | Set array buffer data to the [OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md). |
| [int OH_UdsArrayBuffer_GetData(OH_UdsArrayBuffer* buffer, unsigned char** data, unsigned int* len)](#oh_udsarraybuffer_getdata) | - | Get array buffer data from the [OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md). |
| [OH_UdsContentForm* OH_UdsContentForm_Create()](#oh_udscontentform_create) | - | Creates a pointer to the instance of the [OH_UdsContentForm](capi-udmf-oh-udscontentform.md). |
| [void OH_UdsContentForm_Destroy(OH_UdsContentForm* pThis)](#oh_udscontentform_destroy) | - | Destroy a pointer that points to the [OH_UdsContentForm](capi-udmf-oh-udscontentform.md) instance. |
| [const char* OH_UdsContentForm_GetType(OH_UdsContentForm* pThis)](#oh_udscontentform_gettype) | - | Get type id from the [OH_UdsContentForm](capi-udmf-oh-udscontentform.md). |
| [int OH_UdsContentForm_GetThumbData(OH_UdsContentForm* pThis, unsigned char** thumbData, unsigned int* len)](#oh_udscontentform_getthumbdata) | - | Get thumb data from the [OH_UdsContentForm](capi-udmf-oh-udscontentform.md). |
| [const char* OH_UdsContentForm_GetDescription(OH_UdsContentForm* pThis)](#oh_udscontentform_getdescription) | - | Get description from the [OH_UdsContentForm](capi-udmf-oh-udscontentform.md). |
| [const char* OH_UdsContentForm_GetTitle(OH_UdsContentForm* pThis)](#oh_udscontentform_gettitle) | - | Get title from the [OH_UdsContentForm](capi-udmf-oh-udscontentform.md). |
| [int OH_UdsContentForm_GetAppIcon(OH_UdsContentForm* pThis, unsigned char** appIcon, unsigned int* len)](#oh_udscontentform_getappicon) | - | Obtains the application icon data from an [OH_UdsContentForm](capi-udmf-oh-udscontentform.md) instance. |
| [const char* OH_UdsContentForm_GetAppName(OH_UdsContentForm* pThis)](#oh_udscontentform_getappname) | - | Get app name from the [OH_UdsContentForm](capi-udmf-oh-udscontentform.md). |
| [const char* OH_UdsContentForm_GetLinkUri(OH_UdsContentForm* pThis)](#oh_udscontentform_getlinkuri) | - | Get link url from the [OH_UdsContentForm](capi-udmf-oh-udscontentform.md). |
| [int OH_UdsContentForm_SetThumbData(OH_UdsContentForm* pThis, const unsigned char* thumbData, unsigned int len)](#oh_udscontentform_setthumbdata) | - | Set thumb data to the [OH_UdsContentForm](capi-udmf-oh-udscontentform.md). |
| [int OH_UdsContentForm_SetDescription(OH_UdsContentForm* pThis, const char* description)](#oh_udscontentform_setdescription) | - | Set description to the [OH_UdsContentForm](capi-udmf-oh-udscontentform.md). |
| [int OH_UdsContentForm_SetTitle(OH_UdsContentForm* pThis, const char* title)](#oh_udscontentform_settitle) | - | Set title to the [OH_UdsContentForm](capi-udmf-oh-udscontentform.md). |
| [int OH_UdsContentForm_SetAppIcon(OH_UdsContentForm* pThis, const unsigned char* appIcon, unsigned int len)](#oh_udscontentform_setappicon) | - | Sets the application icon data for an [OH_UdsContentForm](capi-udmf-oh-udscontentform.md) instance. |
| [int OH_UdsContentForm_SetAppName(OH_UdsContentForm* pThis, const char* appName)](#oh_udscontentform_setappname) | - | Set app name to the [OH_UdsContentForm](capi-udmf-oh-udscontentform.md). |
| [int OH_UdsContentForm_SetLinkUri(OH_UdsContentForm* pThis, const char* linkUri)](#oh_udscontentform_setlinkuri) | - | Set link uri to the [OH_UdsContentForm](capi-udmf-oh-udscontentform.md). |
| [OH_UdsDetails* OH_UdsDetails_Create()](#oh_udsdetails_create) | - | Creates a pointer to the instance of the [OH_UdsDetails](capi-udmf-oh-udsdetails.md). |
| [void OH_UdsDetails_Destroy(OH_UdsDetails* pThis)](#oh_udsdetails_destroy) | - | Destroy a pointer that points to the [OH_UdsDetails](capi-udmf-oh-udsdetails.md) instance. |
| [bool OH_UdsDetails_HasKey(const OH_UdsDetails* pThis, const char* key)](#oh_udsdetails_haskey) | - | Determine whether the [OH_UdsDetails](capi-udmf-oh-udsdetails.md) contain the specified key. |
| [int OH_UdsDetails_Remove(OH_UdsDetails* pThis, const char* key)](#oh_udsdetails_remove) | - | Remove the value corresponding to this key from the [OH_UdsDetails](capi-udmf-oh-udsdetails.md). |
| [int OH_UdsDetails_Clear(OH_UdsDetails* pThis)](#oh_udsdetails_clear) | - | Clear all data in the [OH_UdsDetails](capi-udmf-oh-udsdetails.md). |
| [int OH_UdsDetails_SetValue(OH_UdsDetails* pThis, const char* key, const char* value)](#oh_udsdetails_setvalue) | - | Add key-value pair data to the dictionary type [OH_UdsDetails](capi-udmf-oh-udsdetails.md). |
| [const char* OH_UdsDetails_GetValue(const OH_UdsDetails* pThis, const char* key)](#oh_udsdetails_getvalue) | - | Get the value from the [OH_UdsDetails](capi-udmf-oh-udsdetails.md) using the key. |
| [char** OH_UdsDetails_GetAllKeys(OH_UdsDetails* pThis, unsigned int* count)](#oh_udsdetails_getallkeys) | - | Get the all keys from the [OH_UdsDetails](capi-udmf-oh-udsdetails.md). |

## Enum type description

### Udmf_AuthPermission

```c
enum Udmf_AuthPermission
```

**Description**

Enumerates the URI authorization policies in the drag scenario.<br>
> **NOTE**
>
> This authorization policy takes effect only in drag scenarios.<br> The **NONE**, **READ**, **WRITE**, and **PERSIST** policies are supported. They can be combined, and only the following combinations take effect:<br>
- **NONE**: No file permission is granted.
- **READ**: Only one-time read permission is granted.
- **WRITE**: Only one-time read and write permissions are granted. (Write permission includes read permission.)
- **READ+WRITE**: One-time read and write authorization is performed, which is equivalent to **WRITE** authorization.
- **READ+PERSIST**: Persistent read permission is granted.
- **WRITE+PERSIST**: Persistent read and write permissions are granted.
- **READ+WRITE+PERSIST**: Persistent read and write permissions are granted. The rules for applying the drag authorization policies are as follows (in descending order of priority):
- Single data level: The **FileUri** and **HTML** (UDSs) support the configuration of authorization policy parameters, which take effect only once for a single record and have the highest priority.
- [OH_UdmfData](capi-udmf-oh-udmfdata.md) level: The authorization parameters provided in [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md) are valid for a single drag operation. If an authorization policy is configured for a piece of data, the configuration of the data is preferentially used. This level has the second highest priority.
- Default level: If no authorization policy is configured for a single piece of data or [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md), proxy authorization is performed based on the default drag logic. The default logic is as follows:
- FileUri data: By default, the **READ**, **WRITE**, and **PERSIST** permissions are granted in drag scenarios.
- HTML data: Grants read permission only to the URIs in the img tags of the HTML text.

<!--Device-Udmf_AuthPermission--><!--Device-Udmf_AuthPermission-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| UDMF_PERM_NONE = 0 | No permission granted.<br>**Since**: 26.0.0 |
| UDMF_PERM_READ = 1u << 0 | Permission to read or view data.<br>**Since**: 26.0.0 |
| UDMF_PERM_WRITE = 1u << 1 | Permission to modify data (including READ).<br>**Since**: 26.0.0 |
| UDMF_PERM_PERSIST = 1u << 2 | Permission to persist files.<br>**Since**: 26.0.0 |


## Function description

### OH_UDMF_VirtualFileOnStat()

```c
typedef OH_UDMF_VirtualItem* (*OH_UDMF_VirtualFileOnStat)(void* context, const char* id)
```

**Description**

This interface is invoked when virtual file metadata needs to be obtained.<br> The returned node must be created by [OH_UDMF_CreateVirtualFileItem](capi-uds-h.md#oh_udmf_createvirtualfileitem), its ownership is transferred to UDMF, and the node cannot be destroyed after the callback returns.

<!--Device-typedef OH_UDMF_VirtualItem* (*OH_UDMF_VirtualFileOnStat)(void* context, const char* id)--><!--Device-typedef OH_UDMF_VirtualItem* (*OH_UDMF_VirtualFileOnStat)(void* context, const char* id)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| void* context | [in] User context transferred through [OH_UDMF_CreateVirtualFileInfo](capi-uds-h.md#oh_udmf_createvirtualfileinfo). |
| const char* id | [in] ID of the requested virtual file. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UDMF_VirtualItem*](capi-udmf-oh-udmf-virtualitem.md) | Returns the virtual file node on success and nullptr on failure. |

### OH_UDMF_VirtualFileOnRead()

```c
typedef int (*OH_UDMF_VirtualFileOnRead)(void* context, const char* id, int64_t offset, uint32_t length, uint8_t* data, uint32_t* bytesRead)
```

**Description**

This function is invoked when virtual file data needs to be read.<br> A maximum of <code>length</code> bytes can be written to <code>data</code> and the actual number of written bytes can be returned through <code>bytesRead</code>. The actual number of bytes can be less than <code>length</code> or zero.

<!--Device-typedef int (*OH_UDMF_VirtualFileOnRead)(void* context, const char* id, int64_t offset, uint32_t length, uint8_t* data, uint32_t* bytesRead)--><!--Device-typedef int (*OH_UDMF_VirtualFileOnRead)(void* context, const char* id, int64_t offset, uint32_t length, uint8_t* data, uint32_t* bytesRead)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| void* context | [in] User context transferred through [OH_UDMF_CreateVirtualFileInfo](capi-uds-h.md#oh_udmf_createvirtualfileinfo). |
| const char* id | [in] ID of the requested virtual file. |
| int64_t offset | [in] Read offset, in bytes. |
| uint32_t length | [in] Maximum read length. |
| uint8_t* data | [out] Target buffer provided by the UDMF, valid only during callback execution. |
| uint32_t* bytesRead | [out] Number of bytes actually written to <code>data</code>. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Return the execution status code. For details, see [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). <ul> <li>[UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) indicates that the data is successfully read. </li> <li>[UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) indicates that an invalid parameter is transferred. </li> <li>[UDMF_ERR](capi-udmf-err-code-h.md#udmf_errcode) indicates that an internal error occurs and data cannot be provided. </li> </ul> |

**Reference**:

[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)


### OH_UDMF_VirtualFileOnCancel()

```c
typedef int (*OH_UDMF_VirtualFileOnCancel)(void* context, const char* const *idList, uint32_t count)
```

**Description**

Called when a virtual file operation is canceled.

<!--Device-typedef int (*OH_UDMF_VirtualFileOnCancel)(void* context, const char* const *idList, uint32_t count)--><!--Device-typedef int (*OH_UDMF_VirtualFileOnCancel)(void* context, const char* const *idList, uint32_t count)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| void* context | [in] User context transferred through [OH_UDMF_CreateVirtualFileInfo](capi-uds-h.md#oh_udmf_createvirtualfileinfo). |
| const char* const *idList | [in] ID list of canceled virtual files. This array and the strings in it are valid only during the execution of the callback. |
| uint32_t count | [in] Number of identifiers in <code>idList</code>. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Return the execution status code. For details, see [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). <ul> <li>[UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) indicates that the cancellation is successful. </li> <li>[UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) indicates that an invalid parameter is transferred. </li> <li>[UDMF_ERR](capi-udmf-err-code-h.md#udmf_errcode) indicates that an internal error occurs and the cancellation fails. </li> </ul> |

**Reference**:

[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)


### OH_UDMF_VirtualFileFinalize()

```c
typedef void (*OH_UDMF_VirtualFileFinalize)(void* context)
```

**Description**

Releases the user contexts held by the UDMF.<br> This callback is executed only once after all virtual file objects referencing the context are freed. The callback may be executed on any thread.

<!--Device-typedef void (*OH_UDMF_VirtualFileFinalize)(void* context)--><!--Device-typedef void (*OH_UDMF_VirtualFileFinalize)(void* context)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| void* context | [in] UE contexts to be released. |

### OH_UdsPlainText_Create()

```c
OH_UdsPlainText* OH_UdsPlainText_Create()
```

**Description**

Creates an [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md) instance and a pointer to it. If this pointer is no longer required, use {@lOH_UdsPlainText_Destroy} to destroy it. Otherwise, memory leaks may occur.

<!--Device-OH_UdsPlainText* OH_UdsPlainText_Create()--><!--Device-OH_UdsPlainText* OH_UdsPlainText_Create()-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UdsPlainText*](capi-udmf-oh-udsplaintext.md) | If the operation is successful, a pointer to the instance of the [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md) structure is returned. If the operation is failed, nullptr is returned. |

**Reference**:

[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)


### OH_UdsPlainText_Destroy()

```c
void OH_UdsPlainText_Destroy(OH_UdsPlainText* pThis)
```

**Description**

Destroy a pointer that points to the [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md) instance.

<!--Device-void OH_UdsPlainText_Destroy(OH_UdsPlainText* pThis)--><!--Device-void OH_UdsPlainText_Destroy(OH_UdsPlainText* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)* pThis | Represents a pointer to an instance of [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md). |

**Reference**:

[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)


### OH_UdsPlainText_GetType()

```c
const char* OH_UdsPlainText_GetType(OH_UdsPlainText* pThis)
```

**Description**

Get type id from the [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md).

<!--Device-const char* OH_UdsPlainText_GetType(OH_UdsPlainText* pThis)--><!--Device-const char* OH_UdsPlainText_GetType(OH_UdsPlainText* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)* pThis | Represents a pointer to an instance of [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a pointer of the value string when input args normally, otherwise return nullptr. |

**Reference**:

[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)


### OH_UdsPlainText_GetContent()

```c
const char* OH_UdsPlainText_GetContent(OH_UdsPlainText* pThis)
```

**Description**

Get content from the [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md).

<!--Device-const char* OH_UdsPlainText_GetContent(OH_UdsPlainText* pThis)--><!--Device-const char* OH_UdsPlainText_GetContent(OH_UdsPlainText* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)* pThis | Represents a pointer to an instance of [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a pointer of the value string when input args normally, otherwise return nullptr. |

**Reference**:

[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)


### OH_UdsPlainText_GetAbstract()

```c
const char* OH_UdsPlainText_GetAbstract(OH_UdsPlainText* pThis)
```

**Description**

Get abstract from the [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md).

<!--Device-const char* OH_UdsPlainText_GetAbstract(OH_UdsPlainText* pThis)--><!--Device-const char* OH_UdsPlainText_GetAbstract(OH_UdsPlainText* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)* pThis | Represents a pointer to an instance of [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a pointer of the value string when input args normally, otherwise return nullptr. |

**Reference**:

[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)


### OH_UdsPlainText_GetDetails()

```c
int OH_UdsPlainText_GetDetails(OH_UdsPlainText* pThis, OH_UdsDetails* details)
```

**Description**

Get details from the [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md).

<!--Device-int OH_UdsPlainText_GetDetails(OH_UdsPlainText* pThis, OH_UdsDetails* details)--><!--Device-int OH_UdsPlainText_GetDetails(OH_UdsPlainText* pThis, OH_UdsDetails* details)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)* pThis | Represents a pointer to an instance of [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md). |
| [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* details | Represents a pointer to an instance of [OH_UdsDetails](capi-udmf-oh-udsdetails.md). The pointer cannot be null. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsPlainText OH_UdsDetails Udmf_ErrCode


### OH_UdsPlainText_SetContent()

```c
int OH_UdsPlainText_SetContent(OH_UdsPlainText* pThis, const char* content)
```

**Description**

Set content to the [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md).

<!--Device-int OH_UdsPlainText_SetContent(OH_UdsPlainText* pThis, const char* content)--><!--Device-int OH_UdsPlainText_SetContent(OH_UdsPlainText* pThis, const char* content)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)* pThis | Represents a pointer to an instance of [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md). |
| const char* content | Pointer to the plain text content to set. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsPlainText Udmf_ErrCode


### OH_UdsPlainText_SetAbstract()

```c
int OH_UdsPlainText_SetAbstract(OH_UdsPlainText* pThis, const char* abstract)
```

**Description**

Set abstract to the [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md).

<!--Device-int OH_UdsPlainText_SetAbstract(OH_UdsPlainText* pThis, const char* abstract)--><!--Device-int OH_UdsPlainText_SetAbstract(OH_UdsPlainText* pThis, const char* abstract)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)* pThis | Represents a pointer to an instance of [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md). |
| const char* abstract | Represents a new string value. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsPlainText Udmf_ErrCode


### OH_UdsPlainText_SetDetails()

```c
int OH_UdsPlainText_SetDetails(OH_UdsPlainText* pThis, const OH_UdsDetails* details)
```

**Description**

Set details to the [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md).

<!--Device-int OH_UdsPlainText_SetDetails(OH_UdsPlainText* pThis, const OH_UdsDetails* details)--><!--Device-int OH_UdsPlainText_SetDetails(OH_UdsPlainText* pThis, const OH_UdsDetails* details)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)* pThis | Represents a pointer to an instance of [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md). |
| [const OH_UdsDetails](capi-udmf-oh-udsdetails.md)* details | Represents a pointer to an instance of [OH_UdsDetails](capi-udmf-oh-udsdetails.md). The pointer cannot be null. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsPlainText OH_UdsDetails Udmf_ErrCode


### OH_UdsHyperlink_Create()

```c
OH_UdsHyperlink* OH_UdsHyperlink_Create()
```

**Description**

Creates a pointer to the instance of the [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md).

<!--Device-OH_UdsHyperlink* OH_UdsHyperlink_Create()--><!--Device-OH_UdsHyperlink* OH_UdsHyperlink_Create()-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UdsHyperlink*](capi-udmf-oh-udshyperlink.md) | If the operation is successful, a pointer to the instance of [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md) structure is returned. If the operation is failed, nullptr is returned. |

**Reference**:

[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)


### OH_UdsHyperlink_Destroy()

```c
void OH_UdsHyperlink_Destroy(OH_UdsHyperlink* pThis)
```

**Description**

Destroy a pointer that points to the [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md) instance.

<!--Device-void OH_UdsHyperlink_Destroy(OH_UdsHyperlink* pThis)--><!--Device-void OH_UdsHyperlink_Destroy(OH_UdsHyperlink* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)* pThis | Represents a pointer to an  instance of [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md). |

**Reference**:

[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)


### OH_UdsHyperlink_GetType()

```c
const char* OH_UdsHyperlink_GetType(OH_UdsHyperlink* pThis)
```

**Description**

Obtains the type ID from an [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md) instance.

<!--Device-const char* OH_UdsHyperlink_GetType(OH_UdsHyperlink* pThis)--><!--Device-const char* OH_UdsHyperlink_GetType(OH_UdsHyperlink* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)* pThis | Represents a pointer to an instance of [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a pointer of the value string when input args normally, otherwise return nullptr. |

**Reference**:

[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)


### OH_UdsHyperlink_GetUrl()

```c
const char* OH_UdsHyperlink_GetUrl(OH_UdsHyperlink* pThis)
```

**Description**

Get url from the [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md).

<!--Device-const char* OH_UdsHyperlink_GetUrl(OH_UdsHyperlink* pThis)--><!--Device-const char* OH_UdsHyperlink_GetUrl(OH_UdsHyperlink* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)* pThis | Represents a pointer to an instance of [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a pointer of the value string when input args normally, otherwise return nullptr. |

**Reference**:

[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)


### OH_UdsHyperlink_GetDescription()

```c
const char* OH_UdsHyperlink_GetDescription(OH_UdsHyperlink* pThis)
```

**Description**

Get description from the [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md).

<!--Device-const char* OH_UdsHyperlink_GetDescription(OH_UdsHyperlink* pThis)--><!--Device-const char* OH_UdsHyperlink_GetDescription(OH_UdsHyperlink* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)* pThis | Represents a pointer to an instance of [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a pointer of the value string when input args normally, otherwise return nullptr. |

**Reference**:

[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)


### OH_UdsHyperlink_GetDetails()

```c
int OH_UdsHyperlink_GetDetails(OH_UdsHyperlink* pThis, OH_UdsDetails* details)
```

**Description**

Get details from the [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md).

<!--Device-int OH_UdsHyperlink_GetDetails(OH_UdsHyperlink* pThis, OH_UdsDetails* details)--><!--Device-int OH_UdsHyperlink_GetDetails(OH_UdsHyperlink* pThis, OH_UdsDetails* details)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)* pThis | Represents a pointer to an instance of [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md). |
| [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* details | Represents a pointer to an instance of [OH_UdsDetails](capi-udmf-oh-udsdetails.md). The pointer cannot be null. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsHyperlink OH_UdsDetails Udmf_ErrCode


### OH_UdsHyperlink_SetUrl()

```c
int OH_UdsHyperlink_SetUrl(OH_UdsHyperlink* pThis, const char* url)
```

**Description**

Set url to the [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md).

<!--Device-int OH_UdsHyperlink_SetUrl(OH_UdsHyperlink* pThis, const char* url)--><!--Device-int OH_UdsHyperlink_SetUrl(OH_UdsHyperlink* pThis, const char* url)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)* pThis | Represents a pointer to an instance of [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md). |
| const char* url | Represents a new string value. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsHyperlink Udmf_ErrCode


### OH_UdsHyperlink_SetDescription()

```c
int OH_UdsHyperlink_SetDescription(OH_UdsHyperlink* pThis, const char* description)
```

**Description**

Set description to the [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md).

<!--Device-int OH_UdsHyperlink_SetDescription(OH_UdsHyperlink* pThis, const char* description)--><!--Device-int OH_UdsHyperlink_SetDescription(OH_UdsHyperlink* pThis, const char* description)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)* pThis | Represents a pointer to an instance of [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md). |
| const char* description | Represents a new string value. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsHyperlink Udmf_ErrCode


### OH_UdsHyperlink_SetDetails()

```c
int OH_UdsHyperlink_SetDetails(OH_UdsHyperlink* pThis, const OH_UdsDetails* details)
```

**Description**

Set details to the [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md).

<!--Device-int OH_UdsHyperlink_SetDetails(OH_UdsHyperlink* pThis, const OH_UdsDetails* details)--><!--Device-int OH_UdsHyperlink_SetDetails(OH_UdsHyperlink* pThis, const OH_UdsDetails* details)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)* pThis | Represents a pointer to an instance of [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md). |
| [const OH_UdsDetails](capi-udmf-oh-udsdetails.md)* details | Represents a pointer to an instance of [OH_UdsDetails](capi-udmf-oh-udsdetails.md). The pointer cannot be null. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsHyperlink OH_UdsDetails Udmf_ErrCode


### OH_UdsHtml_Create()

```c
OH_UdsHtml* OH_UdsHtml_Create()
```

**Description**

Creates a pointer to the instance of the [OH_UdsHtml](capi-udmf-oh-udshtml.md).

<!--Device-OH_UdsHtml* OH_UdsHtml_Create()--><!--Device-OH_UdsHtml* OH_UdsHtml_Create()-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UdsHtml*](capi-udmf-oh-udshtml.md) | If the operation is successful, a pointer to the instance of the [OH_UdsHtml](capi-udmf-oh-udshtml.md) structure is returned. If the operation is failed, nullptr is returned. |

**Reference**:

[OH_UdsHtml](capi-udmf-oh-udshtml.md)


### OH_UdsHtml_Destroy()

```c
void OH_UdsHtml_Destroy(OH_UdsHtml* pThis)
```

**Description**

Destroy a pointer that points to the [OH_UdsHtml](capi-udmf-oh-udshtml.md) instance.

<!--Device-void OH_UdsHtml_Destroy(OH_UdsHtml* pThis)--><!--Device-void OH_UdsHtml_Destroy(OH_UdsHtml* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsHtml](capi-udmf-oh-udshtml.md)* pThis | Represents a pointer to an instance of [OH_UdsHtml](capi-udmf-oh-udshtml.md). |

**Reference**:

[OH_UdsHtml](capi-udmf-oh-udshtml.md)


### OH_UdsHtml_GetType()

```c
const char* OH_UdsHtml_GetType(OH_UdsHtml* pThis)
```

**Description**

Obtains the type ID from an [OH_UdsHtml](capi-udmf-oh-udshtml.md) instance.

<!--Device-const char* OH_UdsHtml_GetType(OH_UdsHtml* pThis)--><!--Device-const char* OH_UdsHtml_GetType(OH_UdsHtml* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsHtml](capi-udmf-oh-udshtml.md)* pThis | Represents a pointer to an instance of [OH_UdsHtml](capi-udmf-oh-udshtml.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a pointer of the value string when input args normally, otherwise return nullptr. |

**Reference**:

[OH_UdsHtml](capi-udmf-oh-udshtml.md)


### OH_UdsHtml_GetContent()

```c
const char* OH_UdsHtml_GetContent(OH_UdsHtml* pThis)
```

**Description**

Get content from the [OH_UdsHtml](capi-udmf-oh-udshtml.md).

<!--Device-const char* OH_UdsHtml_GetContent(OH_UdsHtml* pThis)--><!--Device-const char* OH_UdsHtml_GetContent(OH_UdsHtml* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsHtml](capi-udmf-oh-udshtml.md)* pThis | Represents a pointer to an instance of [OH_UdsHtml](capi-udmf-oh-udshtml.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a pointer of the value string when input args normally, otherwise return nullptr. |

**Reference**:

[OH_UdsHtml](capi-udmf-oh-udshtml.md)


### OH_UdsHtml_GetPlainContent()

```c
const char* OH_UdsHtml_GetPlainContent(OH_UdsHtml* pThis)
```

**Description**

Get plain content from the [OH_UdsHtml](capi-udmf-oh-udshtml.md).

<!--Device-const char* OH_UdsHtml_GetPlainContent(OH_UdsHtml* pThis)--><!--Device-const char* OH_UdsHtml_GetPlainContent(OH_UdsHtml* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsHtml](capi-udmf-oh-udshtml.md)* pThis | Represents a pointer to an instance of [OH_UdsHtml](capi-udmf-oh-udshtml.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a pointer of the value string when input args normally, otherwise return nullptr. |

**Reference**:

[OH_UdsHtml](capi-udmf-oh-udshtml.md)


### OH_UdsHtml_GetDetails()

```c
int OH_UdsHtml_GetDetails(OH_UdsHtml* pThis, OH_UdsDetails* details)
```

**Description**

Get details from the [OH_UdsHtml](capi-udmf-oh-udshtml.md).

<!--Device-int OH_UdsHtml_GetDetails(OH_UdsHtml* pThis, OH_UdsDetails* details)--><!--Device-int OH_UdsHtml_GetDetails(OH_UdsHtml* pThis, OH_UdsDetails* details)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsHtml](capi-udmf-oh-udshtml.md)* pThis | Represents a pointer to an instance of [OH_UdsHtml](capi-udmf-oh-udshtml.md). |
| [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* details | Represents a pointer to an instance of [OH_UdsDetails](capi-udmf-oh-udsdetails.md). The pointer cannot be null. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsHtml OH_UdsDetails Udmf_ErrCode


### OH_UdsHtml_SetContent()

```c
int OH_UdsHtml_SetContent(OH_UdsHtml* pThis, const char* content)
```

**Description**

Set content to the [OH_UdsHtml](capi-udmf-oh-udshtml.md).

<!--Device-int OH_UdsHtml_SetContent(OH_UdsHtml* pThis, const char* content)--><!--Device-int OH_UdsHtml_SetContent(OH_UdsHtml* pThis, const char* content)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsHtml](capi-udmf-oh-udshtml.md)* pThis | Represents a pointer to an instance of [OH_UdsHtml](capi-udmf-oh-udshtml.md). |
| const char* content | Represents a new string value. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsHtml Udmf_ErrCode


### OH_UdsHtml_SetPlainContent()

```c
int OH_UdsHtml_SetPlainContent(OH_UdsHtml* pThis, const char* plainContent)
```

**Description**

Set plain content to the [OH_UdsHtml](capi-udmf-oh-udshtml.md).

<!--Device-int OH_UdsHtml_SetPlainContent(OH_UdsHtml* pThis, const char* plainContent)--><!--Device-int OH_UdsHtml_SetPlainContent(OH_UdsHtml* pThis, const char* plainContent)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsHtml](capi-udmf-oh-udshtml.md)* pThis | Represents a pointer to an instance of [OH_UdsHtml](capi-udmf-oh-udshtml.md). |
| const char* plainContent | Represents a new string value. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsHtml Udmf_ErrCode


### OH_UdsHtml_SetDetails()

```c
int OH_UdsHtml_SetDetails(OH_UdsHtml* pThis, const OH_UdsDetails* details)
```

**Description**

Set details to the [OH_UdsHtml](capi-udmf-oh-udshtml.md).

<!--Device-int OH_UdsHtml_SetDetails(OH_UdsHtml* pThis, const OH_UdsDetails* details)--><!--Device-int OH_UdsHtml_SetDetails(OH_UdsHtml* pThis, const OH_UdsDetails* details)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsHtml](capi-udmf-oh-udshtml.md)* pThis | Represents a pointer to an instance of [OH_UdsHtml](capi-udmf-oh-udshtml.md). |
| [const OH_UdsDetails](capi-udmf-oh-udsdetails.md)* details | Represents a pointer to an instance of [OH_UdsDetails](capi-udmf-oh-udsdetails.md). The pointer cannot be null. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsHtml OH_UdsDetails Udmf_ErrCode


### OH_UdsHtml_SetAuthPolicy()

```c
int OH_UdsHtml_SetAuthPolicy(OH_UdsHtml* pThis, uint32_t authPolicy)
```

**Description**

Set the authorization policy to [OH_UdsHtml](capi-udmf-oh-udshtml.md).

<!--Device-int OH_UdsHtml_SetAuthPolicy(OH_UdsHtml* pThis, uint32_t authPolicy)--><!--Device-int OH_UdsHtml_SetAuthPolicy(OH_UdsHtml* pThis, uint32_t authPolicy)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsHtml](capi-udmf-oh-udshtml.md)* pThis | Represents a pointer to an instance of [OH_UdsHtml](capi-udmf-oh-udshtml.md). |
| uint32_t authPolicy | URI authorization policy in drag scenarios. The default value is READ (read-only authorization), which takes effect only in scenarios such as the img tag. This policy is used only for a single record and has the highest priority. For details about the policy, see [Udmf_AuthPermission](capi-uds-h.md#udmf_authpermission). |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsHtml Udmf_ErrCode


### OH_UdsAppItem_Create()

```c
OH_UdsAppItem* OH_UdsAppItem_Create()
```

**Description**

Creates a pointer to the instance of the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md).

<!--Device-OH_UdsAppItem* OH_UdsAppItem_Create()--><!--Device-OH_UdsAppItem* OH_UdsAppItem_Create()-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UdsAppItem*](capi-udmf-oh-udsappitem.md) | If the operation is successful, a pointer to the instance of the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md) structure is returned. sIf the operation is failed, nullptr is returned. |

**Reference**:

[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)


### OH_UdsAppItem_Destroy()

```c
void OH_UdsAppItem_Destroy(OH_UdsAppItem* pThis)
```

**Description**

Destroy a pointer that points to the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md) instance.

<!--Device-void OH_UdsAppItem_Destroy(OH_UdsAppItem* pThis)--><!--Device-void OH_UdsAppItem_Destroy(OH_UdsAppItem* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | Represents a pointer to an instance of [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |

**Reference**:

[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)


### OH_UdsAppItem_GetType()

```c
const char* OH_UdsAppItem_GetType(OH_UdsAppItem* pThis)
```

**Description**

Get type from the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md).

<!--Device-const char* OH_UdsAppItem_GetType(OH_UdsAppItem* pThis)--><!--Device-const char* OH_UdsAppItem_GetType(OH_UdsAppItem* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | Represents a pointer to an instance of [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a pointer of the value string when input args normally, otherwise return nullptr. |

**Reference**:

[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)


### OH_UdsAppItem_GetId()

```c
const char* OH_UdsAppItem_GetId(OH_UdsAppItem* pThis)
```

**Description**

Get app id from the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md).

<!--Device-const char* OH_UdsAppItem_GetId(OH_UdsAppItem* pThis)--><!--Device-const char* OH_UdsAppItem_GetId(OH_UdsAppItem* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | Represents a pointer to an instance of [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a pointer of the value string when input args normally, otherwise return nullptr. |

**Reference**:

[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)


### OH_UdsAppItem_GetName()

```c
const char* OH_UdsAppItem_GetName(OH_UdsAppItem* pThis)
```

**Description**

Get app name from the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md).

<!--Device-const char* OH_UdsAppItem_GetName(OH_UdsAppItem* pThis)--><!--Device-const char* OH_UdsAppItem_GetName(OH_UdsAppItem* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | Represents a pointer to an instance of [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a pointer of the value string when input args normally, otherwise return nullptr. |

**Reference**:

[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)


### OH_UdsAppItem_GetIconId()

```c
const char* OH_UdsAppItem_GetIconId(OH_UdsAppItem* pThis)
```

**Description**

Get app icon id from the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md).

<!--Device-const char* OH_UdsAppItem_GetIconId(OH_UdsAppItem* pThis)--><!--Device-const char* OH_UdsAppItem_GetIconId(OH_UdsAppItem* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | Represents a pointer to an instance of [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a pointer of the value string when input args normally, otherwise return nullptr. |

**Reference**:

[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)


### OH_UdsAppItem_GetLabelId()

```c
const char* OH_UdsAppItem_GetLabelId(OH_UdsAppItem* pThis)
```

**Description**

Get app label id from the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md).

<!--Device-const char* OH_UdsAppItem_GetLabelId(OH_UdsAppItem* pThis)--><!--Device-const char* OH_UdsAppItem_GetLabelId(OH_UdsAppItem* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | Represents a pointer to an instance of [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a pointer of the value string when input args normally, otherwise return nullptr. |

**Reference**:

[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)


### OH_UdsAppItem_GetBundleName()

```c
const char* OH_UdsAppItem_GetBundleName(OH_UdsAppItem* pThis)
```

**Description**

Get bundle name from the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md).

<!--Device-const char* OH_UdsAppItem_GetBundleName(OH_UdsAppItem* pThis)--><!--Device-const char* OH_UdsAppItem_GetBundleName(OH_UdsAppItem* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | Represents a pointer to an instance of [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a pointer of the value string when input args normally, otherwise return nullptr. |

**Reference**:

[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)


### OH_UdsAppItem_GetAbilityName()

```c
const char* OH_UdsAppItem_GetAbilityName(OH_UdsAppItem* pThis)
```

**Description**

Get ability name from the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md).

<!--Device-const char* OH_UdsAppItem_GetAbilityName(OH_UdsAppItem* pThis)--><!--Device-const char* OH_UdsAppItem_GetAbilityName(OH_UdsAppItem* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | Represents a pointer to an instance [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a pointer of the value string when input args normally, otherwise return nullptr. |

**Reference**:

[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)


### OH_UdsAppItem_GetDetails()

```c
int OH_UdsAppItem_GetDetails(OH_UdsAppItem* pThis, OH_UdsDetails* details)
```

**Description**

Get details from the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md).

<!--Device-int OH_UdsAppItem_GetDetails(OH_UdsAppItem* pThis, OH_UdsDetails* details)--><!--Device-int OH_UdsAppItem_GetDetails(OH_UdsAppItem* pThis, OH_UdsDetails* details)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | Represents a pointer to an instance of [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |
| [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* details | Represents a pointer to an instance of [OH_UdsDetails](capi-udmf-oh-udsdetails.md). The pointer cannot be null. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsAppItem OH_UdsDetails Udmf_ErrCode


### OH_UdsAppItem_SetId()

```c
int OH_UdsAppItem_SetId(OH_UdsAppItem* pThis, const char* appId)
```

**Description**

Set application id to the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md).

<!--Device-int OH_UdsAppItem_SetId(OH_UdsAppItem* pThis, const char* appId)--><!--Device-int OH_UdsAppItem_SetId(OH_UdsAppItem* pThis, const char* appId)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | Represents a pointer to an instance of [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |
| const char* appId | Represents a new string value. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsAppItem Udmf_ErrCode


### OH_UdsAppItem_SetName()

```c
int OH_UdsAppItem_SetName(OH_UdsAppItem* pThis, const char* appName)
```

**Description**

Set application name to the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md).

<!--Device-int OH_UdsAppItem_SetName(OH_UdsAppItem* pThis, const char* appName)--><!--Device-int OH_UdsAppItem_SetName(OH_UdsAppItem* pThis, const char* appName)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | Represents a pointer to an instance of [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |
| const char* appName | Represents a new string value. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsAppItem Udmf_ErrCode


### OH_UdsAppItem_SetIconId()

```c
int OH_UdsAppItem_SetIconId(OH_UdsAppItem* pThis, const char* appIconId)
```

**Description**

Set application icon id to the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md).

<!--Device-int OH_UdsAppItem_SetIconId(OH_UdsAppItem* pThis, const char* appIconId)--><!--Device-int OH_UdsAppItem_SetIconId(OH_UdsAppItem* pThis, const char* appIconId)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | Represents a pointer to an instance of [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |
| const char* appIconId | Represents a new string value. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsAppItem Udmf_ErrCode


### OH_UdsAppItem_SetLabelId()

```c
int OH_UdsAppItem_SetLabelId(OH_UdsAppItem* pThis, const char* appLabelId)
```

**Description**

Set application label id to the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md).

<!--Device-int OH_UdsAppItem_SetLabelId(OH_UdsAppItem* pThis, const char* appLabelId)--><!--Device-int OH_UdsAppItem_SetLabelId(OH_UdsAppItem* pThis, const char* appLabelId)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | Represents a pointer to an instance of [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |
| const char* appLabelId | Represents a new string value. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsAppItem Udmf_ErrCode


### OH_UdsAppItem_SetBundleName()

```c
int OH_UdsAppItem_SetBundleName(OH_UdsAppItem* pThis, const char* bundleName)
```

**Description**

Set bundle name to the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md).

<!--Device-int OH_UdsAppItem_SetBundleName(OH_UdsAppItem* pThis, const char* bundleName)--><!--Device-int OH_UdsAppItem_SetBundleName(OH_UdsAppItem* pThis, const char* bundleName)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | Represents a pointer to an instance of [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |
| const char* bundleName | Represents a new string value. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsAppItem Udmf_ErrCode


### OH_UdsAppItem_SetAbilityName()

```c
int OH_UdsAppItem_SetAbilityName(OH_UdsAppItem* pThis, const char* abilityName)
```

**Description**

Set ability name to the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md).

<!--Device-int OH_UdsAppItem_SetAbilityName(OH_UdsAppItem* pThis, const char* abilityName)--><!--Device-int OH_UdsAppItem_SetAbilityName(OH_UdsAppItem* pThis, const char* abilityName)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | Represents a pointer to an instance of [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |
| const char* abilityName | Represents a new string value. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsAppItem Udmf_ErrCode


### OH_UdsAppItem_SetDetails()

```c
int OH_UdsAppItem_SetDetails(OH_UdsAppItem* pThis, const OH_UdsDetails* details)
```

**Description**

Set details to the [OH_UdsAppItem](capi-udmf-oh-udsappitem.md).

<!--Device-int OH_UdsAppItem_SetDetails(OH_UdsAppItem* pThis, const OH_UdsDetails* details)--><!--Device-int OH_UdsAppItem_SetDetails(OH_UdsAppItem* pThis, const OH_UdsDetails* details)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | Represents a pointer to an instance of [OH_UdsAppItem](capi-udmf-oh-udsappitem.md). |
| [const OH_UdsDetails](capi-udmf-oh-udsdetails.md)* details | Represents a pointer to an instance of [OH_UdsDetails](capi-udmf-oh-udsdetails.md). The pointer cannot be null. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsAppItem OH_UdsDetails Udmf_ErrCode


### OH_UdsFileUri_Create()

```c
OH_UdsFileUri* OH_UdsFileUri_Create()
```

**Description**

Creates a pointer to the instance of the [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md).

<!--Device-OH_UdsFileUri* OH_UdsFileUri_Create()--><!--Device-OH_UdsFileUri* OH_UdsFileUri_Create()-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 13

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UdsFileUri*](capi-udmf-oh-udsfileuri.md) | If the operation is successful, a pointer to the instance of the [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md) structure is returned. If the memory is not enough, nullptr is returned. |

**Reference**:

[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)


### OH_UdsFileUri_Destroy()

```c
void OH_UdsFileUri_Destroy(OH_UdsFileUri* pThis)
```

**Description**

Destroy a pointer that points to the [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md) instance.

<!--Device-void OH_UdsFileUri_Destroy(OH_UdsFileUri* pThis)--><!--Device-void OH_UdsFileUri_Destroy(OH_UdsFileUri* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)* pThis | Represents a pointer to an instance of [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md). |

**Reference**:

[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)


### OH_UdsFileUri_GetType()

```c
const char* OH_UdsFileUri_GetType(OH_UdsFileUri* pThis)
```

**Description**

Get type id from the [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md).

<!--Device-const char* OH_UdsFileUri_GetType(OH_UdsFileUri* pThis)--><!--Device-const char* OH_UdsFileUri_GetType(OH_UdsFileUri* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)* pThis | Represents a pointer to an instance of [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a pointer of the value string when input args normally, otherwise return nullptr. |

**Reference**:

[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)


### OH_UdsFileUri_GetFileUri()

```c
const char* OH_UdsFileUri_GetFileUri(OH_UdsFileUri* pThis)
```

**Description**

Get file uri from the [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md).

<!--Device-const char* OH_UdsFileUri_GetFileUri(OH_UdsFileUri* pThis)--><!--Device-const char* OH_UdsFileUri_GetFileUri(OH_UdsFileUri* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)* pThis | Represents a pointer to an instance of [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a pointer of the value string when input args normally, otherwise return nullptr. |

**Reference**:

[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)


### OH_UdsFileUri_GetFileType()

```c
const char* OH_UdsFileUri_GetFileType(OH_UdsFileUri* pThis)
```

**Description**

Get file type from the [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md).

<!--Device-const char* OH_UdsFileUri_GetFileType(OH_UdsFileUri* pThis)--><!--Device-const char* OH_UdsFileUri_GetFileType(OH_UdsFileUri* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)* pThis | Represents a pointer to an instance of [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a pointer of the value string when input args normally, otherwise return nullptr. |

**Reference**:

[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)


### OH_UdsFileUri_GetDetails()

```c
int OH_UdsFileUri_GetDetails(OH_UdsFileUri* pThis, OH_UdsDetails* details)
```

**Description**

Get details from the [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md).

<!--Device-int OH_UdsFileUri_GetDetails(OH_UdsFileUri* pThis, OH_UdsDetails* details)--><!--Device-int OH_UdsFileUri_GetDetails(OH_UdsFileUri* pThis, OH_UdsDetails* details)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)* pThis | Represents a pointer to an instance of [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md). |
| [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* details | Represents a pointer to an instance of [OH_UdsDetails](capi-udmf-oh-udsdetails.md). The pointer cannot be null. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsFileUri OH_UdsDetails Udmf_ErrCode


### OH_UdsFileUri_SetFileUri()

```c
int OH_UdsFileUri_SetFileUri(OH_UdsFileUri* pThis, const char* fileUri)
```

**Description**

Set file uri to the [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md).

<!--Device-int OH_UdsFileUri_SetFileUri(OH_UdsFileUri* pThis, const char* fileUri)--><!--Device-int OH_UdsFileUri_SetFileUri(OH_UdsFileUri* pThis, const char* fileUri)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)* pThis | Represents a pointer to an instance of [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md). |
| const char* fileUri | Represents a new file uri string. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsFileUri Udmf_ErrCode


### OH_UdsFileUri_SetFileType()

```c
int OH_UdsFileUri_SetFileType(OH_UdsFileUri* pThis, const char* fileType)
```

**Description**

Set file type to the [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md).

<!--Device-int OH_UdsFileUri_SetFileType(OH_UdsFileUri* pThis, const char* fileType)--><!--Device-int OH_UdsFileUri_SetFileType(OH_UdsFileUri* pThis, const char* fileType)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)* pThis | Represents a pointer to an instance of [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md). |
| const char* fileType | Represents a new file type string. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsFileUri Udmf_ErrCode


### OH_UdsFileUri_SetDetails()

```c
int OH_UdsFileUri_SetDetails(OH_UdsFileUri* pThis, const OH_UdsDetails* details)
```

**Description**

Set details to the [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md).

<!--Device-int OH_UdsFileUri_SetDetails(OH_UdsFileUri* pThis, const OH_UdsDetails* details)--><!--Device-int OH_UdsFileUri_SetDetails(OH_UdsFileUri* pThis, const OH_UdsDetails* details)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)* pThis | Represents a pointer to an instance of [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md). |
| [const OH_UdsDetails](capi-udmf-oh-udsdetails.md)* details | Represents a pointer to an instance of [OH_UdsDetails](capi-udmf-oh-udsdetails.md). The pointer cannot be null. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsFileUri OH_UdsDetails Udmf_ErrCode


### OH_UdsFileUri_SetAuthPolicy()

```c
int OH_UdsFileUri_SetAuthPolicy(OH_UdsFileUri* pThis, uint32_t authPolicy)
```

**Description**

Set the authorization policy to [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md).

<!--Device-int OH_UdsFileUri_SetAuthPolicy(OH_UdsFileUri* pThis, uint32_t authPolicy)--><!--Device-int OH_UdsFileUri_SetAuthPolicy(OH_UdsFileUri* pThis, uint32_t authPolicy)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)* pThis | Represents a pointer to an instance of [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md). |
| uint32_t authPolicy | URI authorization policy in the drag scenario. The default value is READ+WRITE+PERSIST, which is used only for a single record and has the highest priority. For details about the policy, see [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). <br>[UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. <br>[UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsFileUri Udmf_ErrCode


### OH_UDMF_CreateVirtualFileItem()

```c
OH_UDMF_VirtualItem* OH_UDMF_CreateVirtualFileItem(const char* name, const char* id, int64_t modifyTime)
```

**Description**

Create a virtual file node that must explicitly set the file size.<br> Before adding a node to a directory or creating virtual file information, you must call [OH_UDMF_SetVirtualFileSize](capi-uds-h.md#oh_udmf_setvirtualfilesize) to set the file size. A size of zero indicates an empty file, and the file size will not be inferred by other means when the size is not set.

<!--Device-OH_UDMF_VirtualItem* OH_UDMF_CreateVirtualFileItem(const char* name, const char* id, int64_t modifyTime)--><!--Device-OH_UDMF_VirtualItem* OH_UDMF_CreateVirtualFileItem(const char* name, const char* id, int64_t modifyTime)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 26.1.0

**Resource release**: [OH_UDMF_DestroyVirtualItem](#oh_udmf_destroyvirtualitem)

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* name | [in] File name, which cannot contain path separators. |
| const char* id | [in] File ID transferred to the virtual file callback. |
| int64_t modifyTime | [in] Time when the file is modified. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UDMF_VirtualItem*](capi-udmf-oh-udmf-virtualitem.md) | If the operation is successful, the created virtual node is returned. Returns nullptr when the parameter is invalid or memory allocation fails. |

### OH_UDMF_CreateVirtualDirectoryItem()

```c
OH_UDMF_VirtualItem* OH_UDMF_CreateVirtualDirectoryItem(const char* name, int64_t modifyTime)
```

**Description**

Create a virtual directory node.

<!--Device-OH_UDMF_VirtualItem* OH_UDMF_CreateVirtualDirectoryItem(const char* name, int64_t modifyTime)--><!--Device-OH_UDMF_VirtualItem* OH_UDMF_CreateVirtualDirectoryItem(const char* name, int64_t modifyTime)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 26.1.0

**Resource release**: [OH_UDMF_DestroyVirtualItem](#oh_udmf_destroyvirtualitem)

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* name | [in] Directory name, which cannot contain path separators. |
| int64_t modifyTime | [in] Directory modification time. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UDMF_VirtualItem*](capi-udmf-oh-udmf-virtualitem.md) | If the operation is successful, the created virtual node is returned. Returns nullptr when the parameter is invalid or memory allocation fails. |

### OH_UDMF_DestroyVirtualItem()

```c
void OH_UDMF_DestroyVirtualItem(OH_UDMF_VirtualItem* item)
```

**Description**

Destroy a virtual node.

<!--Device-void OH_UDMF_DestroyVirtualItem(OH_UDMF_VirtualItem* item)--><!--Device-void OH_UDMF_DestroyVirtualItem(OH_UDMF_VirtualItem* item)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UDMF_VirtualItem](capi-udmf-oh-udmf-virtualitem.md)* item | [in] Virtual node to be destroyed. |

### OH_UDMF_SetVirtualFileSize()

```c
int OH_UDMF_SetVirtualFileSize(OH_UDMF_VirtualItem* item, int64_t size)
```

**Description**

Set the file size of a virtual file node.

<!--Device-int OH_UDMF_SetVirtualFileSize(OH_UDMF_VirtualItem* item, int64_t size)--><!--Device-int OH_UDMF_SetVirtualFileSize(OH_UDMF_VirtualItem* item, int64_t size)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UDMF_VirtualItem](capi-udmf-oh-udmf-virtualitem.md)* item | [in,out] Virtual file node. |
| int64_t size | [in] File size, in bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Return the execution status code. For details, see [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). <ul> <li>[UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) indicates that the setting is successful. </li> <li>[UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) indicates that <code>item</code> is invalid, is not a file node, or <code>size</code> is a negative number. </li> </ul> |

**Reference**:

[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)


### OH_UDMF_ClearVirtualFileSize()

```c
int OH_UDMF_ClearVirtualFileSize(OH_UDMF_VirtualItem* item)
```

**Description**

The file size that must be set for the virtual file node is cleared during the build process.<br> After clearing, the non-negative file size must be set again via [OH_UDMF_SetVirtualFileSize](capi-uds-h.md#oh_udmf_setvirtualfilesize) before the node can be added to the directory or used to create Virtual file information; The stat callback cannot replace this step.

<!--Device-int OH_UDMF_ClearVirtualFileSize(OH_UDMF_VirtualItem* item)--><!--Device-int OH_UDMF_ClearVirtualFileSize(OH_UDMF_VirtualItem* item)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UDMF_VirtualItem](capi-udmf-oh-udmf-virtualitem.md)* item | [in,out] Virtual file node. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Return the execution status code. For details, see [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). <ul> <li>[UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) indicates that the deletion is successful. </li> <li>[UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) indicates that <code>item</code> is invalid or is not a file node. </li> </ul> |

**Reference**:

[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)


### OH_UDMF_AddVirtualItemChild()

```c
int OH_UDMF_AddVirtualItemChild(OH_UDMF_VirtualItem* directory, const OH_UDMF_VirtualItem* child)
```

**Description**

Adds a child node to the virtual directory.<br> This interface copies <code>child</code>, and the caller still retains the ownership of the original node.

<!--Device-int OH_UDMF_AddVirtualItemChild(OH_UDMF_VirtualItem* directory, const OH_UDMF_VirtualItem* child)--><!--Device-int OH_UDMF_AddVirtualItemChild(OH_UDMF_VirtualItem* directory, const OH_UDMF_VirtualItem* child)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UDMF_VirtualItem](capi-udmf-oh-udmf-virtualitem.md)* directory | [in,out] Virtual directory node. |
| [const OH_UDMF_VirtualItem](capi-udmf-oh-udmf-virtualitem.md)* child | [in] Subnode to be added. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Return the execution status code. For details, see [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). <ul> <li>[UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) indicates that the user is added successfully. </li> <li>[UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) indicates that the node is invalid, <code>directory</code> is not a directory, or the result violates a virtual file tree constraint. </li> </ul> |

**Reference**:

[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)


### OH_UDMF_CreateVirtualFileInfo()

```c
OH_UDMF_VirtualFileInfo* OH_UDMF_CreateVirtualFileInfo(const OH_UDMF_VirtualItem* itemInfo, const OH_UDMF_VirtualFileCallbacks* callbacks, void* context, OH_UDMF_VirtualFileFinalize finalize)
```

**Description**

Create virtual file information.<br> This interface copies the node tree and callback table. <code>finalize</code> must be provided when <code>context</code> is not nullptr. After the interface is successfully executed, the UDMF holds the context until the last reference is released.

<!--Device-OH_UDMF_VirtualFileInfo* OH_UDMF_CreateVirtualFileInfo(const OH_UDMF_VirtualItem* itemInfo, const OH_UDMF_VirtualFileCallbacks* callbacks, void* context, OH_UDMF_VirtualFileFinalize finalize)--><!--Device-OH_UDMF_VirtualFileInfo* OH_UDMF_CreateVirtualFileInfo(const OH_UDMF_VirtualItem* itemInfo, const OH_UDMF_VirtualFileCallbacks* callbacks, void* context, OH_UDMF_VirtualFileFinalize finalize)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 26.1.0

**Resource release**: [OH_UDMF_DestroyVirtualFileInfo](#oh_udmf_destroyvirtualfileinfo)

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_UDMF_VirtualItem](capi-udmf-oh-udmf-virtualitem.md)* itemInfo | [in] Virtual root node. Each file in the tree must explicitly set a non-negative file size. |
| [const OH_UDMF_VirtualFileCallbacks](capi-udmf-oh-udmf-virtualfilecallbacks.md)* callbacks | [in] Virtual file callback. |
| void* context | [in] User context passed to each callback. |
| [OH_UDMF_VirtualFileFinalize](capi-uds-h.md#oh_udmf_virtualfilefinalize) finalize | [in] Callback for releasing <code>context</code>. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UDMF_VirtualFileInfo*](capi-udmf-oh-udmf-virtualfileinfo.md) | If the operation is successful, the information about the created virtual file is returned. Returns nullptr when the node or callback is invalid or memory allocation fails. |

### OH_UDMF_DestroyVirtualFileInfo()

```c
void OH_UDMF_DestroyVirtualFileInfo(OH_UDMF_VirtualFileInfo* info)
```

**Description**

Destroy virtual file information.<br> When virtual file information has been attached to a file URI or unified data record, the callback state remains in effect until all related references are released.

<!--Device-void OH_UDMF_DestroyVirtualFileInfo(OH_UDMF_VirtualFileInfo* info)--><!--Device-void OH_UDMF_DestroyVirtualFileInfo(OH_UDMF_VirtualFileInfo* info)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UDMF_VirtualFileInfo](capi-udmf-oh-udmf-virtualfileinfo.md)* info | [in] Information about the virtual file to be destroyed. |

### OH_UDMF_SetFileUriVirtualEntry()

```c
int OH_UDMF_SetFileUriVirtualEntry(OH_UdsFileUri* fileUri, const OH_UDMF_VirtualFileInfo* info)
```

**Description**

Appends virtual file information to the file URI.

<!--Device-int OH_UDMF_SetFileUriVirtualEntry(OH_UdsFileUri* fileUri, const OH_UDMF_VirtualFileInfo* info)--><!--Device-int OH_UDMF_SetFileUriVirtualEntry(OH_UdsFileUri* fileUri, const OH_UDMF_VirtualFileInfo* info)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)* fileUri | [in,out] URI instance of the file to be updated. |
| [const OH_UDMF_VirtualFileInfo](capi-udmf-oh-udmf-virtualfileinfo.md)* info | [in] Information about the virtual file to be attached. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Return the execution status code. For details, see [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). <ul> <li>[UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) indicates that the attachment is successful. </li> <li>[UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) indicates that <code>fileUri</code> or <code>info</code> is invalid. </li> </ul> |

**Reference**:

[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)


### OH_UDMF_ClearFileUriVirtualEntry()

```c
int OH_UDMF_ClearFileUriVirtualEntry(OH_UdsFileUri* fileUri)
```

**Description**

Removes virtual file information from file URI.

<!--Device-int OH_UDMF_ClearFileUriVirtualEntry(OH_UdsFileUri* fileUri)--><!--Device-int OH_UDMF_ClearFileUriVirtualEntry(OH_UdsFileUri* fileUri)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)* fileUri | [in,out] URI instance of the file to be updated. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Return the execution status code. For details, see [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). <ul> <li>[UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) indicates that the deletion is successful. </li> <li>[UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) indicates that <code>fileUri</code> is invalid. </li> </ul> |

**Reference**:

[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)


### OH_UdsPixelMap_Create()

```c
OH_UdsPixelMap* OH_UdsPixelMap_Create()
```

**Description**

Creates a pointer to the instance of the [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md).

<!--Device-OH_UdsPixelMap* OH_UdsPixelMap_Create()--><!--Device-OH_UdsPixelMap* OH_UdsPixelMap_Create()-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 13

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UdsPixelMap*](capi-udmf-oh-udspixelmap.md) | If the operation is successful, a pointer to the instance of the [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md) structure is returned. If the memory is not enough, nullptr is returned. |

**Reference**:

[OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)


### OH_UdsPixelMap_Destroy()

```c
void OH_UdsPixelMap_Destroy(OH_UdsPixelMap* pThis)
```

**Description**

Destroy a pointer that points to the [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md) instance.

<!--Device-void OH_UdsPixelMap_Destroy(OH_UdsPixelMap* pThis)--><!--Device-void OH_UdsPixelMap_Destroy(OH_UdsPixelMap* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)* pThis | Represents a pointer to an instance of [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md). |

**Reference**:

[OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)


### OH_UdsPixelMap_GetType()

```c
const char* OH_UdsPixelMap_GetType(OH_UdsPixelMap* pThis)
```

**Description**

Get type id from the [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md).

<!--Device-const char* OH_UdsPixelMap_GetType(OH_UdsPixelMap* pThis)--><!--Device-const char* OH_UdsPixelMap_GetType(OH_UdsPixelMap* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)* pThis | Represents a pointer to an instance of [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a pointer of the value string when input args normally, otherwise return nullptr. |

**Reference**:

[OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)


### OH_UdsPixelMap_GetPixelMap()

```c
void OH_UdsPixelMap_GetPixelMap(OH_UdsPixelMap* pThis, OH_PixelmapNative* pixelmapNative)
```

**Description**

Get pixel map from the [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md).

<!--Device-void OH_UdsPixelMap_GetPixelMap(OH_UdsPixelMap* pThis, OH_PixelmapNative* pixelmapNative)--><!--Device-void OH_UdsPixelMap_GetPixelMap(OH_UdsPixelMap* pThis, OH_PixelmapNative* pixelmapNative)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)* pThis | Represents a pointer to an instance of [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md). |
| [OH_PixelmapNative](../../apis-image-kit/c-apis/capi-image-nativemodule-oh-pixelmapnative.md)* pixelmapNative | Represents output params of [OH_PixelmapNative](../../apis-image-kit/c-apis/capi-image-nativemodule-oh-pixelmapnative.md). |

**Reference**:

[OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)


### OH_UdsPixelMap_GetDetails()

```c
int OH_UdsPixelMap_GetDetails(OH_UdsPixelMap* pThis, OH_UdsDetails* details)
```

**Description**

Get details from the [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md).

<!--Device-int OH_UdsPixelMap_GetDetails(OH_UdsPixelMap* pThis, OH_UdsDetails* details)--><!--Device-int OH_UdsPixelMap_GetDetails(OH_UdsPixelMap* pThis, OH_UdsDetails* details)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)* pThis | Represents a pointer to an instance of [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md). |
| [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* details | Represents a pointer to an instance of [OH_UdsDetails](capi-udmf-oh-udsdetails.md). The pointer cannot be null. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsPixelMap OH_UdsDetails Udmf_ErrCode


### OH_UdsPixelMap_SetPixelMap()

```c
int OH_UdsPixelMap_SetPixelMap(OH_UdsPixelMap* pThis, OH_PixelmapNative* pixelmapNative)
```

**Description**

Set pixel map to the [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md).

<!--Device-int OH_UdsPixelMap_SetPixelMap(OH_UdsPixelMap* pThis, OH_PixelmapNative* pixelmapNative)--><!--Device-int OH_UdsPixelMap_SetPixelMap(OH_UdsPixelMap* pThis, OH_PixelmapNative* pixelmapNative)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)* pThis | Represents a pointer to an instance of [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md). |
| [OH_PixelmapNative](../../apis-image-kit/c-apis/capi-image-nativemodule-oh-pixelmapnative.md)* pixelmapNative | Represents a new [OH_PixelmapNative](../../apis-image-kit/c-apis/capi-image-nativemodule-oh-pixelmapnative.md). |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsPixelMap Udmf_ErrCode


### OH_UdsPixelMap_SetDetails()

```c
int OH_UdsPixelMap_SetDetails(OH_UdsPixelMap* pThis, const OH_UdsDetails* details)
```

**Description**

Set details to the [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md).

<!--Device-int OH_UdsPixelMap_SetDetails(OH_UdsPixelMap* pThis, const OH_UdsDetails* details)--><!--Device-int OH_UdsPixelMap_SetDetails(OH_UdsPixelMap* pThis, const OH_UdsDetails* details)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)* pThis | Represents a pointer to an instance of [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md). |
| [const OH_UdsDetails](capi-udmf-oh-udsdetails.md)* details | Represents a pointer to an instance of [OH_UdsDetails](capi-udmf-oh-udsdetails.md). The pointer cannot be null. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsPixelMap OH_UdsDetails Udmf_ErrCode


### OH_UdsArrayBuffer_Create()

```c
OH_UdsArrayBuffer* OH_UdsArrayBuffer_Create()
```

**Description**

Creates a pointer to the instance of the [OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md).

<!--Device-OH_UdsArrayBuffer* OH_UdsArrayBuffer_Create()--><!--Device-OH_UdsArrayBuffer* OH_UdsArrayBuffer_Create()-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 13

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UdsArrayBuffer*](capi-udmf-oh-udsarraybuffer.md) | If the operation is successful, a pointer to the instance of the [OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md) structure is returned. If the memory is not enough, nullptr is returned. |

**Reference**:

[OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md)


### OH_UdsArrayBuffer_Destroy()

```c
int OH_UdsArrayBuffer_Destroy(OH_UdsArrayBuffer* buffer)
```

**Description**

Destroy a pointer that points to the [OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md) instance.

<!--Device-int OH_UdsArrayBuffer_Destroy(OH_UdsArrayBuffer* buffer)--><!--Device-int OH_UdsArrayBuffer_Destroy(OH_UdsArrayBuffer* buffer)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md)* buffer | Represents a pointer to an instance of [OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md). |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsArrayBuffer Udmf_ErrCode


### OH_UdsArrayBuffer_SetData()

```c
int OH_UdsArrayBuffer_SetData(OH_UdsArrayBuffer* buffer, unsigned char* data, unsigned int len)
```

**Description**

Set array buffer data to the [OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md).

<!--Device-int OH_UdsArrayBuffer_SetData(OH_UdsArrayBuffer* buffer, unsigned char* data, unsigned int len)--><!--Device-int OH_UdsArrayBuffer_SetData(OH_UdsArrayBuffer* buffer, unsigned char* data, unsigned int len)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md)* buffer | Represents a pointer to an instance of [OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md). |
| unsigned char* data | Represents the array buffer data. |
| unsigned int len | Represents the length of data param. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsArrayBuffer Udmf_ErrCode


### OH_UdsArrayBuffer_GetData()

```c
int OH_UdsArrayBuffer_GetData(OH_UdsArrayBuffer* buffer, unsigned char** data, unsigned int* len)
```

**Description**

Get array buffer data from the [OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md).

<!--Device-int OH_UdsArrayBuffer_GetData(OH_UdsArrayBuffer* buffer, unsigned char** data, unsigned int* len)--><!--Device-int OH_UdsArrayBuffer_GetData(OH_UdsArrayBuffer* buffer, unsigned char** data, unsigned int* len)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md)* buffer | Represents a pointer to an instance of [OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md). |
| unsigned char** data | Represents a pointer to array buffer data that is a output param. |
| unsigned int* len | Represents the array buffer data length that is a output param. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsArrayBuffer Udmf_ErrCode


### OH_UdsContentForm_Create()

```c
OH_UdsContentForm* OH_UdsContentForm_Create()
```

**Description**

Creates a pointer to the instance of the [OH_UdsContentForm](capi-udmf-oh-udscontentform.md).

<!--Device-OH_UdsContentForm* OH_UdsContentForm_Create()--><!--Device-OH_UdsContentForm* OH_UdsContentForm_Create()-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 14

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UdsContentForm*](capi-udmf-oh-udscontentform.md) | If the operation is successful, a pointer to the instance of the [OH_UdsContentForm](capi-udmf-oh-udscontentform.md) structure is returned. If the operation is failed, nullptr is returned. |

**Reference**:

[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)


### OH_UdsContentForm_Destroy()

```c
void OH_UdsContentForm_Destroy(OH_UdsContentForm* pThis)
```

**Description**

Destroy a pointer that points to the [OH_UdsContentForm](capi-udmf-oh-udscontentform.md) instance.

<!--Device-void OH_UdsContentForm_Destroy(OH_UdsContentForm* pThis)--><!--Device-void OH_UdsContentForm_Destroy(OH_UdsContentForm* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* pThis | Represents a pointer to an instance of [OH_UdsContentForm](capi-udmf-oh-udscontentform.md). |

**Reference**:

[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)


### OH_UdsContentForm_GetType()

```c
const char* OH_UdsContentForm_GetType(OH_UdsContentForm* pThis)
```

**Description**

Get type id from the [OH_UdsContentForm](capi-udmf-oh-udscontentform.md).

<!--Device-const char* OH_UdsContentForm_GetType(OH_UdsContentForm* pThis)--><!--Device-const char* OH_UdsContentForm_GetType(OH_UdsContentForm* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* pThis | Represents a pointer to an instance of [OH_UdsContentForm](capi-udmf-oh-udscontentform.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a pointer of the value string when input args normally, otherwise return nullptr. |

**Reference**:

[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)


### OH_UdsContentForm_GetThumbData()

```c
int OH_UdsContentForm_GetThumbData(OH_UdsContentForm* pThis, unsigned char** thumbData, unsigned int* len)
```

**Description**

Get thumb data from the [OH_UdsContentForm](capi-udmf-oh-udscontentform.md).

<!--Device-int OH_UdsContentForm_GetThumbData(OH_UdsContentForm* pThis, unsigned char** thumbData, unsigned int* len)--><!--Device-int OH_UdsContentForm_GetThumbData(OH_UdsContentForm* pThis, unsigned char** thumbData, unsigned int* len)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* pThis | Represents a pointer to an instance of [OH_UdsContentForm](capi-udmf-oh-udscontentform.md). |
| unsigned char** thumbData | Represents a pointer to thumb data that is a output param. |
| unsigned int* len | Represents the thumb data length that is a output param. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. [UDMF_ERR](capi-udmf-err-code-h.md#udmf_errcode) Internal data error. |

**Reference**:

OH_UdsContentForm Udmf_ErrCode


### OH_UdsContentForm_GetDescription()

```c
const char* OH_UdsContentForm_GetDescription(OH_UdsContentForm* pThis)
```

**Description**

Get description from the [OH_UdsContentForm](capi-udmf-oh-udscontentform.md).

<!--Device-const char* OH_UdsContentForm_GetDescription(OH_UdsContentForm* pThis)--><!--Device-const char* OH_UdsContentForm_GetDescription(OH_UdsContentForm* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* pThis | Represents a pointer to an instance of [OH_UdsContentForm](capi-udmf-oh-udscontentform.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a pointer of the value string when input args normally, otherwise return nullptr. |

**Reference**:

[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)


### OH_UdsContentForm_GetTitle()

```c
const char* OH_UdsContentForm_GetTitle(OH_UdsContentForm* pThis)
```

**Description**

Get title from the [OH_UdsContentForm](capi-udmf-oh-udscontentform.md).

<!--Device-const char* OH_UdsContentForm_GetTitle(OH_UdsContentForm* pThis)--><!--Device-const char* OH_UdsContentForm_GetTitle(OH_UdsContentForm* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* pThis | Represents a pointer to an instance of [OH_UdsContentForm](capi-udmf-oh-udscontentform.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a pointer of the value string when input args normally, otherwise return nullptr. |

**Reference**:

[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)


### OH_UdsContentForm_GetAppIcon()

```c
int OH_UdsContentForm_GetAppIcon(OH_UdsContentForm* pThis, unsigned char** appIcon, unsigned int* len)
```

**Description**

Obtains the application icon data from an [OH_UdsContentForm](capi-udmf-oh-udscontentform.md) instance.

<!--Device-int OH_UdsContentForm_GetAppIcon(OH_UdsContentForm* pThis, unsigned char** appIcon, unsigned int* len)--><!--Device-int OH_UdsContentForm_GetAppIcon(OH_UdsContentForm* pThis, unsigned char** appIcon, unsigned int* len)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* pThis | Represents a pointer to an instance of [OH_UdsContentForm](capi-udmf-oh-udscontentform.md). |
| unsigned char** appIcon | Represents a pointer to app icon that is a output param. |
| unsigned int* len | Represents the app icon length that is a output param. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. [UDMF_ERR](capi-udmf-err-code-h.md#udmf_errcode) Internal data error. |

**Reference**:

OH_UdsContentForm Udmf_ErrCode


### OH_UdsContentForm_GetAppName()

```c
const char* OH_UdsContentForm_GetAppName(OH_UdsContentForm* pThis)
```

**Description**

Get app name from the [OH_UdsContentForm](capi-udmf-oh-udscontentform.md).

<!--Device-const char* OH_UdsContentForm_GetAppName(OH_UdsContentForm* pThis)--><!--Device-const char* OH_UdsContentForm_GetAppName(OH_UdsContentForm* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* pThis | Represents a pointer to an instance of [OH_UdsContentForm](capi-udmf-oh-udscontentform.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a pointer of the value string when input args normally, otherwise return nullptr. |

**Reference**:

[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)


### OH_UdsContentForm_GetLinkUri()

```c
const char* OH_UdsContentForm_GetLinkUri(OH_UdsContentForm* pThis)
```

**Description**

Get link url from the [OH_UdsContentForm](capi-udmf-oh-udscontentform.md).

<!--Device-const char* OH_UdsContentForm_GetLinkUri(OH_UdsContentForm* pThis)--><!--Device-const char* OH_UdsContentForm_GetLinkUri(OH_UdsContentForm* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* pThis | Represents a pointer to an instance of [OH_UdsContentForm](capi-udmf-oh-udscontentform.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a pointer of the value string when input args normally, otherwise return nullptr. |

**Reference**:

[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)


### OH_UdsContentForm_SetThumbData()

```c
int OH_UdsContentForm_SetThumbData(OH_UdsContentForm* pThis, const unsigned char* thumbData, unsigned int len)
```

**Description**

Set thumb data to the [OH_UdsContentForm](capi-udmf-oh-udscontentform.md).

<!--Device-int OH_UdsContentForm_SetThumbData(OH_UdsContentForm* pThis, const unsigned char* thumbData, unsigned int len)--><!--Device-int OH_UdsContentForm_SetThumbData(OH_UdsContentForm* pThis, const unsigned char* thumbData, unsigned int len)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* pThis | Represents a pointer to an instance of [OH_UdsContentForm](capi-udmf-oh-udscontentform.md). |
| const unsigned char* thumbData | Represents the thumb data. |
| unsigned int len | Represents the length of thumb data param. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsContentForm Udmf_ErrCode


### OH_UdsContentForm_SetDescription()

```c
int OH_UdsContentForm_SetDescription(OH_UdsContentForm* pThis, const char* description)
```

**Description**

Set description to the [OH_UdsContentForm](capi-udmf-oh-udscontentform.md).

<!--Device-int OH_UdsContentForm_SetDescription(OH_UdsContentForm* pThis, const char* description)--><!--Device-int OH_UdsContentForm_SetDescription(OH_UdsContentForm* pThis, const char* description)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* pThis | Represents a pointer to an instance of [OH_UdsContentForm](capi-udmf-oh-udscontentform.md). |
| const char* description | Represents a description string. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsContentForm Udmf_ErrCode


### OH_UdsContentForm_SetTitle()

```c
int OH_UdsContentForm_SetTitle(OH_UdsContentForm* pThis, const char* title)
```

**Description**

Set title to the [OH_UdsContentForm](capi-udmf-oh-udscontentform.md).

<!--Device-int OH_UdsContentForm_SetTitle(OH_UdsContentForm* pThis, const char* title)--><!--Device-int OH_UdsContentForm_SetTitle(OH_UdsContentForm* pThis, const char* title)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* pThis | Represents a pointer to an instance of [OH_UdsContentForm](capi-udmf-oh-udscontentform.md). |
| const char* title | Represents a title string. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsContentForm Udmf_ErrCode


### OH_UdsContentForm_SetAppIcon()

```c
int OH_UdsContentForm_SetAppIcon(OH_UdsContentForm* pThis, const unsigned char* appIcon, unsigned int len)
```

**Description**

Sets the application icon data for an [OH_UdsContentForm](capi-udmf-oh-udscontentform.md) instance.

<!--Device-int OH_UdsContentForm_SetAppIcon(OH_UdsContentForm* pThis, const unsigned char* appIcon, unsigned int len)--><!--Device-int OH_UdsContentForm_SetAppIcon(OH_UdsContentForm* pThis, const unsigned char* appIcon, unsigned int len)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* pThis | Represents a pointer to an instance of [OH_UdsContentForm](capi-udmf-oh-udscontentform.md). |
| const unsigned char* appIcon | Represents the app icon. |
| unsigned int len | Represents the length of app icon param. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsContentForm Udmf_ErrCode


### OH_UdsContentForm_SetAppName()

```c
int OH_UdsContentForm_SetAppName(OH_UdsContentForm* pThis, const char* appName)
```

**Description**

Set app name to the [OH_UdsContentForm](capi-udmf-oh-udscontentform.md).

<!--Device-int OH_UdsContentForm_SetAppName(OH_UdsContentForm* pThis, const char* appName)--><!--Device-int OH_UdsContentForm_SetAppName(OH_UdsContentForm* pThis, const char* appName)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* pThis | Represents a pointer to an instance of [OH_UdsContentForm](capi-udmf-oh-udscontentform.md). |
| const char* appName | Represents a app name string. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsContentForm Udmf_ErrCode


### OH_UdsContentForm_SetLinkUri()

```c
int OH_UdsContentForm_SetLinkUri(OH_UdsContentForm* pThis, const char* linkUri)
```

**Description**

Set link uri to the [OH_UdsContentForm](capi-udmf-oh-udscontentform.md).

<!--Device-int OH_UdsContentForm_SetLinkUri(OH_UdsContentForm* pThis, const char* linkUri)--><!--Device-int OH_UdsContentForm_SetLinkUri(OH_UdsContentForm* pThis, const char* linkUri)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* pThis | Represents a pointer to an instance of [OH_UdsContentForm](capi-udmf-oh-udscontentform.md). |
| const char* linkUri | Represents a link uri string. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsContentForm Udmf_ErrCode


### OH_UdsDetails_Create()

```c
OH_UdsDetails* OH_UdsDetails_Create()
```

**Description**

Creates a pointer to the instance of the [OH_UdsDetails](capi-udmf-oh-udsdetails.md).

<!--Device-OH_UdsDetails* OH_UdsDetails_Create()--><!--Device-OH_UdsDetails* OH_UdsDetails_Create()-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 22

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UdsDetails*](capi-udmf-oh-udsdetails.md) | If the operation is successful, a pointer to the instance of the [OH_UdsDetails](capi-udmf-oh-udsdetails.md) structure is returned. If the operation is failed, nullptr is returned. |

**Reference**:

[OH_UdsDetails](capi-udmf-oh-udsdetails.md)


### OH_UdsDetails_Destroy()

```c
void OH_UdsDetails_Destroy(OH_UdsDetails* pThis)
```

**Description**

Destroy a pointer that points to the [OH_UdsDetails](capi-udmf-oh-udsdetails.md) instance.

<!--Device-void OH_UdsDetails_Destroy(OH_UdsDetails* pThis)--><!--Device-void OH_UdsDetails_Destroy(OH_UdsDetails* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* pThis | Represents a pointer to an instance of [OH_UdsDetails](capi-udmf-oh-udsdetails.md). |

**Reference**:

[OH_UdsDetails](capi-udmf-oh-udsdetails.md)


### OH_UdsDetails_HasKey()

```c
bool OH_UdsDetails_HasKey(const OH_UdsDetails* pThis, const char* key)
```

**Description**

Determine whether the [OH_UdsDetails](capi-udmf-oh-udsdetails.md) contain the specified key.

<!--Device-bool OH_UdsDetails_HasKey(const OH_UdsDetails* pThis, const char* key)--><!--Device-bool OH_UdsDetails_HasKey(const OH_UdsDetails* pThis, const char* key)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_UdsDetails](capi-udmf-oh-udsdetails.md)* pThis | Represents a pointer to an instance of the [OH_UdsDetails](capi-udmf-oh-udsdetails.md). |
| const char* key | Represents key in the details. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns the status code of the execution. {@code false} Represents The details do not contain the key. {@code true} Represents The details contain the key. |

**Reference**:

[OH_UdsDetails](capi-udmf-oh-udsdetails.md)


### OH_UdsDetails_Remove()

```c
int OH_UdsDetails_Remove(OH_UdsDetails* pThis, const char* key)
```

**Description**

Remove the value corresponding to this key from the [OH_UdsDetails](capi-udmf-oh-udsdetails.md).

<!--Device-int OH_UdsDetails_Remove(OH_UdsDetails* pThis, const char* key)--><!--Device-int OH_UdsDetails_Remove(OH_UdsDetails* pThis, const char* key)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* pThis | Represents a pointer to an instance of [OH_UdsDetails](capi-udmf-oh-udsdetails.md). |
| const char* key | Represents key in the details. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsDetails Udmf_ErrCode


### OH_UdsDetails_Clear()

```c
int OH_UdsDetails_Clear(OH_UdsDetails* pThis)
```

**Description**

Clear all data in the [OH_UdsDetails](capi-udmf-oh-udsdetails.md).

<!--Device-int OH_UdsDetails_Clear(OH_UdsDetails* pThis)--><!--Device-int OH_UdsDetails_Clear(OH_UdsDetails* pThis)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* pThis | Represents a pointer to an instance of [OH_UdsDetails](capi-udmf-oh-udsdetails.md). |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). [UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode) success. [UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode) The error code for common invalid args. |

**Reference**:

OH_UdsDetails Udmf_ErrCode


### OH_UdsDetails_SetValue()

```c
int OH_UdsDetails_SetValue(OH_UdsDetails* pThis, const char* key, const char* value)
```

**Description**

Add key-value pair data to the dictionary type [OH_UdsDetails](capi-udmf-oh-udsdetails.md).

<!--Device-int OH_UdsDetails_SetValue(OH_UdsDetails* pThis, const char* key, const char* value)--><!--Device-int OH_UdsDetails_SetValue(OH_UdsDetails* pThis, const char* key, const char* value)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* pThis | Represents a pointer to an instance of the dictionary type [OH_UdsDetails](capi-udmf-oh-udsdetails.md). |
| const char* key | Represents the key of a key-value pair in a dictionary type. |
| const char* value | [in] indicates the value of the key-value pair in the dictionary type. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. <br>If UDMF_E_OK is returned, the operation is successful. <br>If UDMF_E_INVALID_PARAM is returned, an invalid parameter is transferred. For details, see [Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode). |

**Reference**:

OH_UdsDetails Udmf_ErrCode


### OH_UdsDetails_GetValue()

```c
const char* OH_UdsDetails_GetValue(const OH_UdsDetails* pThis, const char* key)
```

**Description**

Get the value from the [OH_UdsDetails](capi-udmf-oh-udsdetails.md) using the key.

<!--Device-const char* OH_UdsDetails_GetValue(const OH_UdsDetails* pThis, const char* key)--><!--Device-const char* OH_UdsDetails_GetValue(const OH_UdsDetails* pThis, const char* key)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_UdsDetails](capi-udmf-oh-udsdetails.md)* pThis | Represents a pointer to an instance of [OH_UdsDetails](capi-udmf-oh-udsdetails.md). |
| const char* key | Represents key in the details. |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a string pointer when input args normally, otherwise return nullptr. |

**Reference**:

[OH_UdsDetails](capi-udmf-oh-udsdetails.md)


### OH_UdsDetails_GetAllKeys()

```c
char** OH_UdsDetails_GetAllKeys(OH_UdsDetails* pThis, unsigned int* count)
```

**Description**

Get the all keys from the [OH_UdsDetails](capi-udmf-oh-udsdetails.md).

<!--Device-char** OH_UdsDetails_GetAllKeys(OH_UdsDetails* pThis, unsigned int* count)--><!--Device-char** OH_UdsDetails_GetAllKeys(OH_UdsDetails* pThis, unsigned int* count)-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* pThis | Represents a pointer to an instance of [OH_UdsDetails](capi-udmf-oh-udsdetails.md). |
| unsigned int* count | Represents the keys count. |

**Returns**:

| Type | Description |
| -- | -- |
| char** | Returns a double pointer to the result set if the operation is successful; <br>returns nullptr otherwise. <br>When [OH_UdsDetails_Destroy](capi-uds-h.md#oh_udsdetails_destroy) is used to destroy the [OH_UdsDetails](capi-udmf-oh-udsdetails.md) instance, the return value is also released. |

**Reference**:

[OH_UdsDetails](capi-udmf-oh-udsdetails.md)



