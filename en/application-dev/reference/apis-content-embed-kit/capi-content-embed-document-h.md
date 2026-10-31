# content_embed_document.h

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->

## Overview

Provides the data structures and corresponding operation APIs related to the embedded documents (OE documents) implemented using the OE technology.<br>This module uses the hierarchical storage structure of **Document**-**Storage**-**Stream**. **Document** is the top-level container. **Storage** is similar to a directory in a file system and can contain the sub-storage and stream. **Stream** is similar to a file and supports binary data read and write.

**File to include:** <ContentEmbedKit/content_embed/content_embed_document.h>

**Library:** libcontent_embed_ndk.so

**System capability:** SystemCapability.ContentEmbed.ObjectEditor

**Since:** 24

**Related module:** [ContentEmbed](capi-contentembed.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) | ContentEmbed_Document | Defines the struct of an OE document. This struct encapsulates the metadata, content, and storage structure of an embedded document. It is used to manage the data of embedded documents in a unified manner within an app, facilitating access, parsing, and storage of the embedded documents.<br>You can select a method based on the data source:<br>Use [OH_ContentEmbed_CreateDocumentByOEid](capi-content-embed-document-h.md#oh_contentembed_createdocumentbyoeid) if you have the OEID.<br>Use [OH_ContentEmbed_CreateDocumentByFile](capi-content-embed-document-h.md#oh_contentembed_createdocumentbyfile) if you have the source file and need to embed or link it.<br>Use [OH_ContentEmbed_LoadDocumentFromFile](capi-content-embed-document-h.md#oh_contentembed_loaddocumentfromfile) if you have a saved OE file.|
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) | ContentEmbed_Storage | Defines the **Storage** struct of an OE document. Similar to a directory in a file system, this struct is used to organize and manage hierarchical data in an OE document. Except for the root storage, the parent object of a storage object must be another storage object. This is applicable to scenarios where nested storage and document element organization are required.<br>Create a [ContentEmbed_Document](capi-contentembed-contentembed-document.md) instance and then obtain the root storage object using [OH_ContentEmbed_Document_GetRootStorage](capi-content-embed-document-h.md#oh_contentembed_document_getrootstorage).<br>Use [OH_ContentEmbed_Storage_CreateStorage](capi-content-embed-document-h.md#oh_contentembed_storage_createstorage) to create a sub-storage object in the OE document based on the storage object and name, or use [OH_ContentEmbed_Storage_GetStorage](capi-content-embed-document-h.md#oh_contentembed_storage_getstorage) to obtain a sub-storage object from the OE document.|
| [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) | ContentEmbed_StorageElement | Defines the storage element struct of an OE document. After obtaining the object instance from [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) using [OH_ContentEmbed_StorageElements_GetElement](capi-content-embed-document-h.md#oh_contentembed_storageelements_getelement), you can use [OH_ContentEmbed_StorageElement_GetName](capi-content-embed-document-h.md#oh_contentembed_storageelement_getname) to obtain the name, [OH_ContentEmbed_StorageElement_GetCTime](capi-content-embed-document-h.md#oh_contentembed_storageelement_getctime) to obtain the creation time, and [OH_ContentEmbed_StorageElement_GetMTime](capi-content-embed-document-h.md#oh_contentembed_storageelement_getmtime) to obtain the modification time.<br>After checking whether the current element is an encapsulated object of [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) by using [OH_ContentEmbed_StorageElement_IsStorage](capi-content-embed-document-h.md#oh_contentembed_storageelement_isstorage), you can use [OH_ContentEmbed_Storage_GetStorage](capi-content-embed-document-h.md#oh_contentembed_storage_getstorage) to obtain a sub-storage object from the OE document.<br>After checking whether the current element is an encapsulated object of [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) using [OH_ContentEmbed_StorageElement_IsStream](capi-content-embed-document-h.md#oh_contentembed_storageelement_isstream), you can use [OH_ContentEmbed_Storage_GetStream](capi-content-embed-document-h.md#oh_contentembed_storage_getstream) to obtain a stream object from the OE document.|
| [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) | ContentEmbed_StorageElements | Defines the **ContentEmbed_StorageElements** struct. This struct obtains all [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) and [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) objects under a [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) object through [OH_ContentEmbed_Storage_GetElements](capi-content-embed-document-h.md#oh_contentembed_storage_getelements). Each object is encapsulated into a [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) struct. You can use [OH_ContentEmbed_StorageElements_GetCount](capi-content-embed-document-h.md#oh_contentembed_storageelements_getcount) to obtain the number of elements in the current query and [OH_ContentEmbed_StorageElements_GetElement](capi-content-embed-document-h.md#oh_contentembed_storageelements_getelement) to obtain the [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance object at a specified index position.|
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) | ContentEmbed_Stream | Defines the **Stream** struct of an OE document. Similar to a file in the file system, data can be read from or written to this struct. A stream object can exist only in a storage object. This struct is applicable to scenarios where OE document content is read or written in stream mode in a storage object. Use [OH_ContentEmbed_Storage_CreateStream](capi-content-embed-document-h.md#oh_contentembed_storage_createstream) to create a stream object in the OE document based on the storage object and name, or use [OH_ContentEmbed_Storage_GetStream](capi-content-embed-document-h.md#oh_contentembed_storage_getstream) to obtain a stream object from the OE document.|

### Macros

| Name| Description|
| -- | -- |
| MAX_PATH_LENGTH (4 * 1024) | Maximum length of a file path.<br>**Since:** 24|

### Functions

| Name| Description|
| -- | -- |
| [ContentEmbed_ErrorCode OH_ContentEmbed_CreateDocumentByOEid(const char *oeid, ContentEmbed_Document **document)](#oh_contentembed_createdocumentbyoeid) | Creates a new [ContentEmbed_Document](capi-contentembed-contentembed-document.md) instance using the provided OEID.<br>You can call [OH_ContentEmbed_DestroyDocument](capi-content-embed-document-h.md#oh_contentembed_destroydocument) to destroy the instance to prevent memory leaks.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_CreateDocumentByFile(const char *srcFilePath, size_t length, bool isLinking, ContentEmbed_Document **document)](#oh_contentembed_createdocumentbyfile) | Creates a new [ContentEmbed_Document](capi-contentembed-contentembed-document.md) instance from a source file.<br>You can call [OH_ContentEmbed_DestroyDocument](capi-content-embed-document-h.md#oh_contentembed_destroydocument) to destroy the instance to prevent memory leaks.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_LoadDocumentFromFile(const char *srcFilePath, size_t length, ContentEmbed_Document **document)](#oh_contentembed_loaddocumentfromfile) | Loads a [ContentEmbed_Document](capi-contentembed-contentembed-document.md) instance from an existing OE file.<br>You can call [OH_ContentEmbed_DestroyDocument](capi-content-embed-document-h.md#oh_contentembed_destroydocument) to destroy the instance to prevent memory leaks.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Document_Read(uint8_t *buffer, size_t length, ContentEmbed_Document *document, size_t offset, size_t *readSize)](#oh_contentembed_document_read) | Reads raw binary data from the specified offset position of an OE document object to the buffer. This method is applicable to scenarios where direct access to the original binary content of a document is required, such as document backup, data transmission, or custom parsing.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Document_GetOEid(const ContentEmbed_Document *document, char *oeid)](#oh_contentembed_document_getoeid) | Obtains the OEID from an OE document object.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Document_IsLinking(const ContentEmbed_Document *document, bool *isLinking)](#oh_contentembed_document_islinking) | Checks whether an OE document is created in link mode.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Document_GetNativeFilePath(const ContentEmbed_Document *document, char *nativeFilePath)](#oh_contentembed_document_getnativefilepath) | Obtains the path of the embedded source file stored in the client sandbox directory from an OE document. This method is applicable to scenarios where the embedded source file needs to be directly accessed or operated, such as file preview or secondary editing.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Document_GetRootStorage(ContentEmbed_Document *document, ContentEmbed_Storage **storage)](#oh_contentembed_document_getrootstorage) | Obtains the root [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) object from an OE document object.<br>You can call [OH_ContentEmbed_DestroyStorage](capi-content-embed-document-h.md#oh_contentembed_destroystorage) to destroy the instance to prevent memory leaks.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Document_Flush(const ContentEmbed_Document *document)](#oh_contentembed_document_flush) | Flushes data in an OE document to an OE file. You are advised to call this API after modifying the storage or stream object of an OE document to ensure that the modified content is persistently saved. If this API is not called, the modified data may be lost.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_CreateStorage(const ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Storage **childStorage)](#oh_contentembed_storage_createstorage) | Creates a child [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) object based on the parent storage object and name of an OE document.<br>You can call [OH_ContentEmbed_DestroyStorage](capi-content-embed-document-h.md#oh_contentembed_destroystorage) to destroy the instance to prevent memory leaks.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetStorage(const ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Storage **childStorage)](#oh_contentembed_storage_getstorage) | Obtains a child [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) object based on the parent storage object and name of an OE document.<br>Unlike [OH_ContentEmbed_Storage_CreateStorage](capi-content-embed-document-h.md#oh_contentembed_storage_createstorage), this API is used to obtain existing storage objects in an OE document.<br>You can call [OH_ContentEmbed_DestroyStorage](capi-content-embed-document-h.md#oh_contentembed_destroystorage) to destroy the instance to prevent memory leaks.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_CreateStream(ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Stream **childStream)](#oh_contentembed_storage_createstream) | Creates a [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) object based on the parent storage object and name of an OE document.<br>You can destroy an instance using [OH_ContentEmbed_DestroyStream](capi-content-embed-document-h.md#oh_contentembed_destroystream) to avoid memory leaks.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetStream(ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Stream **childStream)](#oh_contentembed_storage_getstream) | Obtains a child [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) object from the parent storage object and name of an OE document.<br>Different from [OH_ContentEmbed_Storage_CreateStream](capi-content-embed-document-h.md#oh_contentembed_storage_createstream), this API is used to obtain existing child stream objects in an OE document.<br>You can destroy an instance using [OH_ContentEmbed_DestroyStream](capi-content-embed-document-h.md#oh_contentembed_destroystream) to avoid memory leaks.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_DeleteEntry(ContentEmbed_Storage *parentStorage, const char *name)](#oh_contentembed_storage_deleteentry) | Deletes a child storage or stream object with a specified name from the parent storage object of an OE document. This method is applicable to scenarios where the internal storage structure of an OE document needs to be cleared or reorganized. Exercise caution because deleted data cannot be restored.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_DeleteAllEntry(ContentEmbed_Storage *storage)](#oh_contentembed_storage_deleteallentry) | Deletes all entries from the storage object of an OE document, including child storage and stream objects. This method is applicable to scenarios where all content of the storage object needs to be cleared. Deleted data cannot be restored. Exercise caution when performing this operation.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyStorage(ContentEmbed_Storage *storage)](#oh_contentembed_destroystorage) | Destroys an [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) instance of an OE document and reclaims the memory.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Stream_Read(ContentEmbed_Stream *stream, unsigned char **buffer, size_t length, size_t *num)](#oh_contentembed_stream_read) | Reads data of a specified length from the current position of the stream object of an OE document to the buffer. After the read operation is successful, the offset of the stream object increases based on the actual number of read bytes.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Stream_Write(ContentEmbed_Stream *stream, const unsigned char *data, size_t length, size_t *num)](#oh_contentembed_stream_write) | Writes data of a specified length from the buffer to the current position of the stream object of an OE document. After the write operation is successful, the offset of the stream object increases based on the actual number of written bytes.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Stream_Seek(ContentEmbed_Stream *stream, size_t position)](#oh_contentembed_stream_seek) | Sets the current position of the stream object of an OE document to a specified offset. This method is applicable to scenarios where specific location data in a stream needs to be accessed randomly. It is often used together with read or write operations.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Stream_GetPosition(ContentEmbed_Stream *stream, size_t *position)](#oh_contentembed_stream_getposition) | Obtains the current position offset of the stream object of an OE document.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Stream_GetSize(ContentEmbed_Stream *stream, size_t *size)](#oh_contentembed_stream_getsize) | Obtains the total size of the stream object of an OE document, in bytes.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyStream(ContentEmbed_Stream *stream)](#oh_contentembed_destroystream) | Destroys a [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) instance of an OE document and reclaims the memory.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyDocument(ContentEmbed_Document *document)](#oh_contentembed_destroydocument) | Destroys a [ContentEmbed_Document](capi-contentembed-contentembed-document.md) instance and reclaims the memory.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetOEid(ContentEmbed_Storage *storage, char *oeid, size_t oeidSize)](#oh_contentembed_storage_getoeid) | Obtains the OEID of the document to which the OE document storage object belongs.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_SetOEid(ContentEmbed_Storage *storage, char *oeid, size_t oeidSize)](#oh_contentembed_storage_setoeid) | Sets the OEID of the document to which the OE document storage object belongs.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_Create(ContentEmbed_StorageElements **storageElements)](#oh_contentembed_storageelements_create) | Creates and initializes a [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) instance.<br>You can destroy an instance using [OH_ContentEmbed_StorageElements_Destroy](capi-content-embed-document-h.md#oh_contentembed_storageelements_destroy) to avoid memory leaks.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_Destroy(ContentEmbed_StorageElements *storageElements)](#oh_contentembed_storageelements_destroy) | Destroys a [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) instance and reclaims the memory.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetElements(const ContentEmbed_Storage *storage, ContentEmbed_StorageElements *storageElements)](#oh_contentembed_storage_getelements) | Obtains the elements in the storage object of an OE document.<br>You need to call [OH_ContentEmbed_StorageElements_Create](capi-content-embed-document-h.md#oh_contentembed_storageelements_create) to create a [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) instance first. After calling this method to fill elements in the storage object to the **StorageElements** instance, you can use [OH_ContentEmbed_StorageElements_GetCount](capi-content-embed-document-h.md#oh_contentembed_storageelements_getcount) to obtain the number of elements. Call [OH_ContentEmbed_StorageElements_GetElement](capi-content-embed-document-h.md#oh_contentembed_storageelements_getelement) to obtain the element at the specified index. After the operation, you can destroy an instance using [OH_ContentEmbed_StorageElements_Destroy](capi-content-embed-document-h.md#oh_contentembed_storageelements_destroy) to avoid memory leaks.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_GetCount(const ContentEmbed_StorageElements *storageElements, size_t *count)](#oh_contentembed_storageelements_getcount) | Obtains the number of elements in a [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) instance.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_GetElement(const ContentEmbed_StorageElements *storageElements, size_t index, ContentEmbed_StorageElement **storageElement)](#oh_contentembed_storageelements_getelement) | Obtains the element at a specified index in a [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) instance.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_GetName(const ContentEmbed_StorageElement *storageElement, char *name, size_t nameSize)](#oh_contentembed_storageelement_getname) | Obtains the name of a [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_GetCTime(const ContentEmbed_StorageElement *element, uint64_t *ctime)](#oh_contentembed_storageelement_getctime) | Obtains the creation timestamp of a [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance, in milliseconds.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_GetMTime(const ContentEmbed_StorageElement *element, uint64_t *mtime)](#oh_contentembed_storageelement_getmtime) | Obtains the last modification timestamp of a [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance, in milliseconds.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_IsStorage(const ContentEmbed_StorageElement *storageElement, bool *isStorage)](#oh_contentembed_storageelement_isstorage) | Checks whether a [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance is an OE document storage object.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_IsStream(const ContentEmbed_StorageElement *element, bool *isStream)](#oh_contentembed_storageelement_isstream) | Checks whether a [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance is an OE document stream object.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_CopyTo(ContentEmbed_Storage *srcStorage, ContentEmbed_Storage *destStorage)](#oh_contentembed_storage_copyto) | Copies all child storage and stream objects from the storage object of a source OE document to the storage object of a target OE document. This operation is a recursive deep copy, which copies all child levels. If an item with the same name already exists in the target storage, the original content will be overwritten.|

## Function Description

### OH_ContentEmbed_CreateDocumentByOEid()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_CreateDocumentByOEid(const char *oeid, ContentEmbed_Document **document)
```

**Description**

Creates a new [ContentEmbed_Document](capi-contentembed-contentembed-document.md) instance using the provided OEID.<br>You can call [OH_ContentEmbed_DestroyDocument](capi-content-embed-document-h.md#oh_contentembed_destroydocument) to destroy the instance to prevent memory leaks.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| const char *oeid | Unique identifier of an OE document (OEID). It is recommended that the array length be [MAX_OEID_LENGTH](capi-content-embed-common-h.md#macros).|
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) **document |  Pointer to the newly created OE document object. This is an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_CreateDocumentByFile()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_CreateDocumentByFile(const char *srcFilePath, size_t length, bool isLinking, ContentEmbed_Document **document)
```

**Description**

Creates a new [ContentEmbed_Document](capi-contentembed-contentembed-document.md) instance from a source file.<br>You can call [OH_ContentEmbed_DestroyDocument](capi-content-embed-document-h.md#oh_contentembed_destroydocument) to destroy the instance to prevent memory leaks.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| const char *srcFilePath | Source file path. When **isLinking** is set to **true**, the sandbox path cannot be passed. Otherwise, the **CE_ERR_INVALID_LINKING_PATH** error is returned.|
| size_t length | Length of the source file path string, excluding the terminator. The value must be greater than 0.|
| bool isLinking | Whether the OE document is created in link mode. **true:** The OE document is created in link mode. When the server edits the OE document, the source file is also modified.<br>                  **false:** The OE document is created in embedded mode. When the client requests the server to edit the OE document, a temporary file is copied to the app sandbox directory on the client.|
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) **document |  Pointer to the newly created OE document object. This is an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.<br>     **CE_ERR_INVALID_LINKING_PATH**: The link file is in the app sandbox and the link cannot be created.|

### OH_ContentEmbed_LoadDocumentFromFile()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_LoadDocumentFromFile(const char *srcFilePath, size_t length, ContentEmbed_Document **document)
```

**Description**

Loads a [ContentEmbed_Document](capi-contentembed-contentembed-document.md) instance from an existing OE file.<br>You can call [OH_ContentEmbed_DestroyDocument](capi-content-embed-document-h.md#oh_contentembed_destroydocument) to destroy the instance to prevent memory leaks.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| const char *srcFilePath | Source file path, which points to the OE file to be loaded. The value cannot be an empty string.|
| size_t length | Length of the source file path string, excluding the terminator. The value must be greater than 0.|
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) **document |  Pointer to the newly created OE document object. This is an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Document_Read()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Document_Read(uint8_t *buffer, size_t length, ContentEmbed_Document *document, size_t offset, size_t *readSize)
```

**Description**

Reads raw binary data from the specified offset position of an OE document object to the buffer. This method is applicable to scenarios where direct access to the original binary content of a document is required, such as document backup, data transmission, or custom parsing.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| uint8_t *buffer |  Buffer for storing the data read from the OE document. This is an output parameter.|
| size_t length | Buffer size, in bytes. When the length is 0, a success message is returned and 0 bytes are actually read.|
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | Pointer to the OE document object.|
| size_t offset | Offset from which data starts to be read in an OE document, in bytes. The value starts from 0.|
| size_t *readSize |  Length of the data that is actually read, in bytes. This is an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_STORAGE_OPERATION_FAILED**: An operation on the storage object of the OE document failed.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Document_GetOEid()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Document_GetOEid(const ContentEmbed_Document *document, char *oeid)
```

**Description**

Obtains the OEID from an OE document object.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [const ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | Pointer to the OE document object.|
| char *oeid |  Array used to store the OEID values. This is an output parameter. It is recommended that the array length be [MAX_OEID_LENGTH](capi-content-embed-common-h.md#macros).|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Document_IsLinking()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Document_IsLinking(const ContentEmbed_Document *document, bool *isLinking)
```

**Description**

Checks whether an OE document is created in link mode.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [const ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | Pointer to the OE document object.|
| bool *isLinking | Output parameter. The value **true** indicates that the OE document is created in link mode, and **false** indicates that the OE document is created in non-link mode.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Document_GetNativeFilePath()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Document_GetNativeFilePath(const ContentEmbed_Document *document, char *nativeFilePath)
```

**Description**

Obtains the path of the embedded source file stored in the client sandbox directory from an OE document. This method is applicable to scenarios where the embedded source file needs to be directly accessed or operated, such as file preview or secondary editing.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [const ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | Pointer to the OE document object.|
| char *nativeFilePath |  Array used to store the source file path. This is an output parameter. It is recommended that the array length be [MAX_PATH_LENGTH](#macros).|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Document_GetRootStorage()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Document_GetRootStorage(ContentEmbed_Document *document, ContentEmbed_Storage **storage)
```

**Description**

Obtains the root [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) object from an OE document object.<br>You can call [OH_ContentEmbed_DestroyStorage](capi-content-embed-document-h.md#oh_contentembed_destroystorage) to destroy the instance to prevent memory leaks.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | Pointer to the OE document object.|
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) **storage |  Pointer to the root storage object of the OE document. This is an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Document_Flush()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Document_Flush(const ContentEmbed_Document *document)
```

**Description**

Flushes data in an OE document to an OE file. You are advised to call this API after modifying the storage or stream object of an OE document to ensure that the modified content is persistently saved. If this API is not called, the modified data may be lost.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [const ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | Pointer to the OE document object.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_FILE_OPERATION_FAILED**: The file operation fails.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Storage_CreateStorage()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_CreateStorage(const ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Storage **childStorage)
```

**Description**

Creates a child [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) object based on the parent storage object and name of an OE document.<br>You can call [OH_ContentEmbed_DestroyStorage](capi-content-embed-document-h.md#oh_contentembed_destroystorage) to destroy the instance to prevent memory leaks.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [const ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *parentStorage | Pointer to the parent storage object of the OE document.<br>                      To delete a specified child storage object from the parent storage object, call [OH_ContentEmbed_Storage_DeleteEntry](capi-content-embed-document-h.md#oh_contentembed_storage_deleteentry).<br>                      To delete all child storage objects from the parent storage object, call [OH_ContentEmbed_Storage_DeleteAllEntry](capi-content-embed-document-h.md#oh_contentembed_storage_deleteallentry).|
| const char *name | Name of the child storage to be created. The value cannot be an empty string, exceed 31 characters, or contain the following invalid characters: /\\:!|
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) **childStorage |  Pointer to the newly created child storage object of the OE document. This is an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails. The possible cause is that the parent storage object is invalid or the name is invalid.<br>     **CE_ERR_NULL_POINTER**: The pointer is null. The possible cause is that the child storage object fails to be created.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_STORAGE_OPERATION_FAILED**: An operation on the storage object of the OE document failed.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Storage_GetStorage()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetStorage(const ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Storage **childStorage)
```

**Description**

Obtains a child [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) object based on the parent storage object and name of an OE document.<br>Unlike [OH_ContentEmbed_Storage_CreateStorage](capi-content-embed-document-h.md#oh_contentembed_storage_createstorage), this API is used to obtain existing storage objects in an OE document.<br>You can call [OH_ContentEmbed_DestroyStorage](capi-content-embed-document-h.md#oh_contentembed_destroystorage) to destroy the instance to prevent memory leaks.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [const ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *parentStorage | Pointer to the parent storage object of the OE document.|
| const char *name | Name of the child storage object to be obtained. The value cannot be an empty string, exceed 31 characters, or contain the following invalid characters: /\\:!|
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) **childStorage |  Pointer to the child storage object of the OE document. This is an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_STORAGE_OPERATION_FAILED**: An operation on the storage object of the OE document failed.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Storage_CreateStream()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_CreateStream(ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Stream **childStream)
```

**Description**

Creates a [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) object based on the parent storage object and name of an OE document.<br>You can destroy an instance using [OH_ContentEmbed_DestroyStream](capi-content-embed-document-h.md#oh_contentembed_destroystream) to avoid memory leaks.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *parentStorage | Pointer to the parent storage object of the OE document.<br>                      To delete a specified child stream object from the parent storage object, call [OH_ContentEmbed_Storage_DeleteEntry](capi-content-embed-document-h.md#oh_contentembed_storage_deleteentry).<br>                      To delete all child stream objects from the parent storage object, call [OH_ContentEmbed_Storage_DeleteAllEntry](capi-content-embed-document-h.md#oh_contentembed_storage_deleteallentry).|
| const char *name | Name of the stream object to be created, which is used to identify and search for the stream. The value cannot be an empty string, exceed 31 characters, or contain the following invalid characters: /\\:!|
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) **childStream |  Pointer to the newly created stream object of the OE document. This is an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_STORAGE_OPERATION_FAILED**: An operation on the storage object of the OE document failed.<br>     **CE_ERR_STREAM_OPERATION_FAILED**: An operation on the stream object of the OE document failed.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Storage_GetStream()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetStream(ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Stream **childStream)
```

**Description**

Obtains a child [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) object from the parent storage object and name of an OE document.<br>Different from [OH_ContentEmbed_Storage_CreateStream](capi-content-embed-document-h.md#oh_contentembed_storage_createstream), this API is used to obtain existing child stream objects in an OE document.<br>You can destroy an instance using [OH_ContentEmbed_DestroyStream](capi-content-embed-document-h.md#oh_contentembed_destroystream) to avoid memory leaks.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *parentStorage | Pointer to the parent storage object of the OE document.|
| const char *name | Name of the OE document stream object to be obtained. The value cannot be an empty string, exceed 31 characters, or contain the following invalid characters: /\\:!|
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) **childStream |  Pointer to the stream object of the OE document. This is an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_STORAGE_OPERATION_FAILED**: An operation on the storage object of the OE document failed.<br>     **CE_ERR_STREAM_OPERATION_FAILED**: An operation on the stream object of the OE document failed.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Storage_DeleteEntry()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_DeleteEntry(ContentEmbed_Storage *parentStorage, const char *name)
```

**Description**

Deletes a child storage or stream object with a specified name from the parent storage object of an OE document. This method is applicable to scenarios where the internal storage structure of an OE document needs to be cleared or reorganized. Exercise caution because deleted data cannot be restored.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *parentStorage | Pointer to the parent storage object of the OE document.|
| const char *name | Name of the child storage or stream object to be deleted. The value cannot be an empty string, exceed 31 characters, or contain the following invalid characters: /\\:!|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_STORAGE_OPERATION_FAILED**: An operation on the storage object of the OE document failed.<br>     **CE_ERR_FILE_OPERATION_FAILED**: The file operation fails.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Storage_DeleteAllEntry()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_DeleteAllEntry(ContentEmbed_Storage *storage)
```

**Description**

Deletes all entries from the storage object of an OE document, including child storage and stream objects. This method is applicable to scenarios where all content of the storage object needs to be cleared. Deleted data cannot be restored. Exercise caution when performing this operation.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *storage | Pointer to the storage object of an OE document.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_STORAGE_OPERATION_FAILED**: An operation on the storage object of the OE document failed.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_DestroyStorage()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_DestroyStorage(ContentEmbed_Storage *storage)
```

**Description**

Destroys an [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) instance of an OE document and reclaims the memory.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *storage | Pointer to the storage object of an OE document.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Stream_Read()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Stream_Read(ContentEmbed_Stream *stream, unsigned char **buffer, size_t length, size_t *num)
```

**Description**

Reads data of a specified length from the current position of the stream object of an OE document to the buffer. After the read operation is successful, the offset of the stream object increases based on the actual number of read bytes.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) *stream | Pointer to the stream object of an OE document.|
| unsigned char **buffer |  Pointer to the buffer that stores the read data. This is an output parameter. Memory is allocated inside the function. The caller is responsible for freeing the memory.|
| size_t length | Maximum number of bytes to read. The value must be greater than 0.|
| size_t *num |  Length of the data that is actually read, in bytes. This is an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_STREAM_OPERATION_FAILED**: An operation on the stream object of the OE document failed.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Stream_Write()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Stream_Write(ContentEmbed_Stream *stream, const unsigned char *data, size_t length, size_t *num)
```

**Description**

Writes data of a specified length from the buffer to the current position of the stream object of an OE document. After the write operation is successful, the offset of the stream object increases based on the actual number of written bytes.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) *stream | Pointer to the stream object of an OE document.|
| const unsigned char *data |  Pointer to the buffer to which data is to be written. This is an input parameter.|
| size_t length | Size of written data, in bytes. When the length is 0, a success message is returned and 0 bytes are written.|
| size_t *num |  Length of the data that is actually written, in bytes. This is an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_STREAM_OPERATION_FAILED**: An operation on the stream object of the OE document failed.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Stream_Seek()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Stream_Seek(ContentEmbed_Stream *stream, size_t position)
```

**Description**

Sets the current position of the stream object of an OE document to a specified offset. This method is applicable to scenarios where specific location data in a stream needs to be accessed randomly. It is often used together with read or write operations.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) *stream | Pointer to the stream object of an OE document.|
| size_t position | Offset of the stream object relative to the start position, in bytes. The value starts from 0. The value cannot exceed the size returned by [OH_ContentEmbed_Stream_GetSize](capi-content-embed-document-h.md#oh_contentembed_stream_getsize) of the stream object.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_STREAM_OPERATION_FAILED**: An operation on the stream object of the OE document failed.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Stream_GetPosition()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Stream_GetPosition(ContentEmbed_Stream *stream, size_t *position)
```

**Description**

Obtains the current position offset of the stream object of an OE document.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) *stream | Pointer to the stream object of an OE document.|
| size_t *position |  Offset of the stream object relative to the start position, in bytes, starting from 0. This is an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_STREAM_OPERATION_FAILED**: An operation on the stream object of the OE document failed.<br>     **CE_ERR_FILE_OPERATION_FAILED**: The file operation fails.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Stream_GetSize()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Stream_GetSize(ContentEmbed_Stream *stream, size_t *size)
```

**Description**

Obtains the total size of the stream object of an OE document, in bytes.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) *stream | Pointer to the stream object of an OE document.|
| size_t *size |  Total size of the stream object of an OE document, in bytes. This is an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_STREAM_OPERATION_FAILED**: An operation on the stream object of the OE document failed.<br>     **CE_ERR_FILE_OPERATION_FAILED**: The file operation fails.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_DestroyStream()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_DestroyStream(ContentEmbed_Stream *stream)
```

**Description**

Destroys a [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) instance of an OE document and reclaims the memory.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) *stream | Pointer to the stream object of an OE document.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_DestroyDocument()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_DestroyDocument(ContentEmbed_Document *document)
```

**Description**

Destroys a [ContentEmbed_Document](capi-contentembed-contentembed-document.md) instance and reclaims the memory.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | Pointer to the OE document object.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Storage_GetOEid()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetOEid(ContentEmbed_Storage *storage, char *oeid, size_t oeidSize)
```

**Description**

Obtains the OEID of the document to which the OE document storage object belongs.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *storage | Pointer to the storage object of an OE document.|
| char *oeid |  Array for storing OEIDs. This is an output parameter. It is recommended that the array length be [MAX_OEID_LENGTH](capi-content-embed-common-h.md#macros).|
| size_t oeidSize | Length of the OEID array, in bytes.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_STORAGE_OPERATION_FAILED**: An operation on the storage object of the OE document failed.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Storage_SetOEid()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_SetOEid(ContentEmbed_Storage *storage, char *oeid, size_t oeidSize)
```

**Description**

Sets the OEID of the document to which the OE document storage object belongs.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *storage | Pointer to the storage object of an OE document.|
| char *oeid | Array of the OEIDs to be set. It is recommended that the array length be [MAX_OEID_LENGTH](capi-content-embed-common-h.md#macros).|
| size_t oeidSize | Length of the OEID array, in bytes.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_STORAGE_OPERATION_FAILED**: An operation on the storage object of the OE document failed.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_StorageElements_Create()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_Create(ContentEmbed_StorageElements **storageElements)
```

**Description**

Creates and initializes a [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) instance.<br>You can destroy an instance using [OH_ContentEmbed_StorageElements_Destroy](capi-content-embed-document-h.md#oh_contentembed_storageelements_destroy) to avoid memory leaks.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) **storageElements |  Pointer to the [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) instance. This is an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_StorageElements_Destroy()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_Destroy(ContentEmbed_StorageElements *storageElements)
```

**Description**

Destroys a [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) instance and reclaims the memory.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) *storageElements | Pointer to the [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) instance.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Storage_GetElements()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetElements(const ContentEmbed_Storage *storage, ContentEmbed_StorageElements *storageElements)
```

**Description**

Obtains the elements in the storage object of an OE document.<br>You need to call [OH_ContentEmbed_StorageElements_Create](capi-content-embed-document-h.md#oh_contentembed_storageelements_create) to create a [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) instance first. After calling this method to fill elements in the storage object to the **StorageElements** instance, you can use [OH_ContentEmbed_StorageElements_GetCount](capi-content-embed-document-h.md#oh_contentembed_storageelements_getcount) to obtain the number of elements. Call [OH_ContentEmbed_StorageElements_GetElement](capi-content-embed-document-h.md#oh_contentembed_storageelements_getelement) to obtain the element at the specified index. After the operation, you can destroy an instance using [OH_ContentEmbed_StorageElements_Destroy](capi-content-embed-document-h.md#oh_contentembed_storageelements_destroy) to avoid memory leaks.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [const ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *storage | Pointer to the storage object of an OE document.|
| [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) *storageElements | Elements in the storage object of an OE document.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_STORAGE_OPERATION_FAILED**: An operation on the storage object of the OE document failed.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_StorageElements_GetCount()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_GetCount(const ContentEmbed_StorageElements *storageElements, size_t *count)
```

**Description**

Obtains the number of elements in a [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) instance.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [const ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) *storageElements | Pointer to the [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) instance.|
| size_t *count |  Number of elements in the storage element set. This is an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_StorageElements_GetElement()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_GetElement(const ContentEmbed_StorageElements *storageElements, size_t index, ContentEmbed_StorageElement **storageElement)
```

**Description**

Obtains the element at a specified index in a [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) instance.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [const ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) *storageElements | Pointer to the [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) instance.|
| size_t index | Index of the element to obtain, starting from 0. The index range is [0, **count** – 1], where **count** can be obtained by calling [OH_ContentEmbed_StorageElements_GetCount](capi-content-embed-document-h.md#oh_contentembed_storageelements_getcount).|
| [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) **storageElement |  Pointer to the [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance. This is an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_StorageElement_GetName()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_GetName(const ContentEmbed_StorageElement *storageElement, char *name, size_t nameSize)
```

**Description**

Obtains the name of a [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [const ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) *storageElement | Pointer to the [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance.|
| char *name |  Element name string. This is an output parameter.|
| size_t nameSize | Size of the name buffer, in bytes.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_StorageElement_GetCTime()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_GetCTime(const ContentEmbed_StorageElement *element, uint64_t *ctime)
```

**Description**

Obtains the creation timestamp of a [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance, in milliseconds.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [const ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) *element | Pointer to the [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance.|
| uint64_t *ctime |  Pointer to the creation timestamp of the element, in milliseconds. This is an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_StorageElement_GetMTime()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_GetMTime(const ContentEmbed_StorageElement *element, uint64_t *mtime)
```

**Description**

Obtains the last modification timestamp of a [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance, in milliseconds.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [const ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) *element | Pointer to the [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance.|
| uint64_t *mtime |  Pointer to the last modification timestamp of the element, in milliseconds. This is an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_StorageElement_IsStorage()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_IsStorage(const ContentEmbed_StorageElement *storageElement, bool *isStorage)
```

**Description**

Checks whether a [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance is an OE document storage object.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [const ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) *storageElement | Pointer to the [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance.|
| bool *isStorage | Output parameter. The value **true** indicates that the object is an OE document storage object, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_StorageElement_IsStream()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_IsStream(const ContentEmbed_StorageElement *element, bool *isStream)
```

**Description**

Checks whether a [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance is an OE document stream object.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [const ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) *element | Pointer to the [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance.|
| bool *isStream | Output parameter. The value **true** indicates that the object is an OE document stream object, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Storage_CopyTo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_CopyTo(ContentEmbed_Storage *srcStorage, ContentEmbed_Storage *destStorage)
```

**Description**

Copies all child storage and stream objects from the storage object of a source OE document to the storage object of a target OE document. This operation is a recursive deep copy, which copies all child levels. If an item with the same name already exists in the target storage, the original content will be overwritten.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *srcStorage | Pointer to the storage object of the source OE document.|
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *destStorage | Pointer to the storage object of the target OE document.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_STORAGE_OPERATION_FAILED**: An operation on the storage object of the OE document failed.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|
