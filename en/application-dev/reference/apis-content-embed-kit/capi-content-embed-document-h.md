# content_embed_document.h

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->

## Overview

Provides the data structures and corresponding operation APIs related to the embedded documents (OE documents) implemented using the OE technology.

**File to include**: <ContentEmbedKit/content_embed/content_embed_document.h>

**Library**: libcontent_embed_ndk.so

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Related module**: [ContentEmbed](capi-contentembed.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) | ContentEmbed_Document | Defines the structure type of an OE document. Encapsulates the metadata, content, and storage structure of an embedded document.|
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) | ContentEmbed_Storage | Defines the storage structure type of an OE document. Similar to a directory in the file system, the parent object of a storage object must be another storage object or the root storage object.|
| [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) | ContentEmbed_StorageElement | Defines the structure type of a storage element in an OE document. It contains information such as the name, type, and time.|
| [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) | ContentEmbed_StorageElements | Declares the ContentEmbed_StorageElements structure. Contains the [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) set information.|
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) | ContentEmbed_Stream | Declares the Stream structure type of an OE document. Similar to a file in the file system, a stream can be read or written. A stream object can exist only in a storage object.|

### Macros

| Name| Description|
| -- | -- |
| MAX_PATH_LENGTH (4 * 1024) | Indicates the maximum length of a file path.<br>**Since**: 24|

### Functions

| Name| Description|
| -- | -- |
| [ContentEmbed_ErrorCode OH_ContentEmbed_CreateDocumentByOEid(const char *oeid, ContentEmbed_Document **document)](#oh_contentembed_createdocumentbyoeid) | Creates a new [ContentEmbed_Document](capi-contentembed-contentembed-document.md) instance using the provided identifier (OEID).<br> You can destroy the instance using [OH_ContentEmbed_DestroyDocument](capi-content-embed-document-h.md#oh_contentembed_destroydocument) to avoid memory leaks.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_CreateDocumentByFile(const char *srcFilePath, size_t length, bool isLinking, ContentEmbed_Document **document)](#oh_contentembed_createdocumentbyfile) | Creates a new [ContentEmbed_Document](capi-contentembed-contentembed-document.md) instance from a source file.<br> You can destroy the instance using [OH_ContentEmbed_DestroyDocument](capi-content-embed-document-h.md#oh_contentembed_destroydocument) to avoid memory leaks.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_LoadDocumentFromFile(const char *srcFilePath, size_t length, ContentEmbed_Document **document)](#oh_contentembed_loaddocumentfromfile) | Loads a [ContentEmbed_Document](capi-contentembed-contentembed-document.md) instance from an existing .oe file.<br> You can destroy the instance using [OH_ContentEmbed_DestroyDocument](capi-content-embed-document-h.md#oh_contentembed_destroydocument) to avoid memory leaks.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Document_Read(uint8_t *buffer, size_t length, ContentEmbed_Document *document, size_t offset, size_t *readSize)](#oh_contentembed_document_read) | Reads the original binary data from the specified offset position of the.oe file to the buffer.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Document_GetOEid(const ContentEmbed_Document *document, char *oeid)](#oh_contentembed_document_getoeid) | Obtains the identifier of an OE document object.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Document_IsLinking(const ContentEmbed_Document *document, bool *isLinking)](#oh_contentembed_document_islinking) | Checks whether an OE document is created in link mode.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Document_GetNativeFilePath(const ContentEmbed_Document *document, char *nativeFilePath)](#oh_contentembed_document_getnativefilepath) | Obtains the path of the embedded source file stored in the sandbox directory of the client from the OE document.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Document_GetRootStorage(ContentEmbed_Document *document, ContentEmbed_Storage **storage)](#oh_contentembed_document_getrootstorage) | Obtains the root [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) object from the OE document object.<br> You can destroy the instance using [OH_ContentEmbed_DestroyStorage](capi-content-embed-document-h.md#oh_contentembed_destroystorage) to avoid memory leaks.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Document_Flush(const ContentEmbed_Document *document)](#oh_contentembed_document_flush) | Flushes data in an OE document to an OE file.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_CreateStorage(const ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Storage **childStorage)](#oh_contentembed_storage_createstorage) | Creates a child [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) object based on the parent Storage object and name of the OE document.<br> You can destroy the instance using [OH_ContentEmbed_DestroyStorage](capi-content-embed-document-h.md#oh_contentembed_destroystorage) to avoid memory leaks.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetStorage(const ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Storage **childStorage)](#oh_contentembed_storage_getstorage) | Obtains a child [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) object from the parent Storage object and name of the OE document.<br> You can destroy the instance using [OH_ContentEmbed_DestroyStorage](capi-content-embed-document-h.md#oh_contentembed_destroystorage) to avoid memory leaks.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_CreateStream(ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Stream **childStream)](#oh_contentembed_storage_createstream) | Creates a [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) object from the parent Storage object and name in the OE document.<br> You can destroy the instance using [OH_ContentEmbed_DestroyStream](capi-content-embed-document-h.md#oh_contentembed_destroystream) to avoid memory leaks.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetStream(ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Stream **childStream)](#oh_contentembed_storage_getstream) | Obtains a child [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) object from the parent Storage object and name in the OE document.<br> You can destroy the instance using [OH_ContentEmbed_DestroyStream](capi-content-embed-document-h.md#oh_contentembed_destroystream) to avoid memory leaks.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_DeleteEntry(ContentEmbed_Storage *parentStorage, const char *name)](#oh_contentembed_storage_deleteentry) | Deletes a child Storage object or Stream object with a specified name from the parent Storage object in the OpenHarmony document.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_DeleteAllEntry(ContentEmbed_Storage *storage)](#oh_contentembed_storage_deleteallentry) | Deletes all entries from the storage object of an OpenEdge document, including the sub-storage objects and sub-stream objects.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyStorage(ContentEmbed_Storage *storage)](#oh_contentembed_destroystorage) | Destroys the [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) object instance of an OpenEdge document and reclaims the memory.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Stream_Read(ContentEmbed_Stream *stream, unsigned char **buffer, size_t length, size_t *num)](#oh_contentembed_stream_read) | Reads data of a specified length from the current position of the stream object of an OpenEdge document to the buffer. After the data is successfully read, the offset of the stream object increases by the number of actually read bytes.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Stream_Write(ContentEmbed_Stream *stream, const unsigned char *data, size_t length, size_t *num)](#oh_contentembed_stream_write) | Writes data of a specified length from the buffer to the current position of the stream object of an OpenEdge document. After the data is successfully written, the offset of the stream object increases by the number of actually written bytes.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Stream_Seek(ContentEmbed_Stream *stream, size_t position)](#oh_contentembed_stream_seek) | Sets the current read location of the stream object in an OE document to the specified offset.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Stream_GetPosition(ContentEmbed_Stream *stream, size_t *position)](#oh_contentembed_stream_getposition) | Obtains the current position offset of the stream object in an OE document.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Stream_GetSize(ContentEmbed_Stream *stream, size_t *size)](#oh_contentembed_stream_getsize) | Obtains the total size of the stream object in an OE document, in bytes.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyStream(ContentEmbed_Stream *stream)](#oh_contentembed_destroystream) | Destroys the [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) object instance of an OE document and reclaims the memory.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyDocument(ContentEmbed_Document *document)](#oh_contentembed_destroydocument) | Destroys the [ContentEmbed_Document](capi-contentembed-contentembed-document.md) object instance and reclaims the memory.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetOEid(ContentEmbed_Storage *storage, char *oeid, size_t oeidSize)](#oh_contentembed_storage_getoeid) | Obtains the identifier (OEID) of the storage object in an OE document.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_SetOEid(ContentEmbed_Storage *storage, char *oeid, size_t oeidSize)](#oh_contentembed_storage_setoeid) | Sets the identifier of the storage object in the OE document.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_Create(ContentEmbed_StorageElements **storageElements)](#oh_contentembed_storageelements_create) | Creates and initializes an [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) instance.<br> You can destroy the instance using [OH_ContentEmbed_StorageElements_Destroy](capi-content-embed-document-h.md#oh_contentembed_storageelements_destroy) to avoid memory leaks.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_Destroy(ContentEmbed_StorageElements *storageElements)](#oh_contentembed_storageelements_destroy) | Destroys the [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) instance and reclaims the occupied memory.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetElements(const ContentEmbed_Storage *storage, ContentEmbed_StorageElements *storageElements)](#oh_contentembed_storage_getelements) | Obtains the element list in the Storage object of the OE document.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_GetCount(const ContentEmbed_StorageElements *storageElements, size_t *count)](#oh_contentembed_storageelements_getcount) | Obtains the number of elements in the [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) instance.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_GetElement(const ContentEmbed_StorageElements *storageElements, size_t index, ContentEmbed_StorageElement **storageElement)](#oh_contentembed_storageelements_getelement) | Obtains the element at the specified index position in the [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) instance.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_GetName(const ContentEmbed_StorageElement *storageElement, char *name, size_t nameSize)](#oh_contentembed_storageelement_getname) | Obtains the name of the [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_GetCTime(const ContentEmbed_StorageElement *element, uint64_t *ctime)](#oh_contentembed_storageelement_getctime) | Obtains the creation timestamp of the [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance, in milliseconds.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_GetMTime(const ContentEmbed_StorageElement *element, uint64_t *mtime)](#oh_contentembed_storageelement_getmtime) | Obtains the last modification timestamp of the [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance, in milliseconds.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_IsStorage(const ContentEmbed_StorageElement *storageElement, bool *isStorage)](#oh_contentembed_storageelement_isstorage) | Checks whether the [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance is an object of the Storage class in the OE document.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_IsStream(const ContentEmbed_StorageElement *element, bool *isStream)](#oh_contentembed_storageelement_isstream) | Checks whether the [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance is a stream object of the OE document.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_CopyTo(ContentEmbed_Storage *srcStorage, ContentEmbed_Storage *destStorage)](#oh_contentembed_storage_copyto) | Copies all sub-storage objects and stream objects from the source OE document storage object to the target OE document storage object.|

## Function Description

### OH_ContentEmbed_CreateDocumentByOEid()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_CreateDocumentByOEid(const char *oeid, ContentEmbed_Document **document)
```

**Description**

Creates a new [ContentEmbed_Document](capi-contentembed-contentembed-document.md) instance using the provided identifier OEID.<br> You can destroy the instance using [OH_ContentEmbed_DestroyDocument](capi-content-embed-document-h.md#oh_contentembed_destroydocument) to avoid memory leaks.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| const char *oeid | Identifier of the OE document, which is used to uniquely identify the OE document. It is recommended that the array length be [MAX_OEID_LENGTH](capi-content-embed-common-h.md#macros).|
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) **document | Output parameter. This pointer points to the newly created OE document object.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The following error codes are returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_CreateDocumentByFile()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_CreateDocumentByFile(const char *srcFilePath, size_t length, bool isLinking, ContentEmbed_Document **document)
```

**Description**

Creates a new [ContentEmbed_Document](capi-contentembed-contentembed-document.md) instance from a source file.<br> You can destroy the instance using [OH_ContentEmbed_DestroyDocument](capi-content-embed-document-h.md#oh_contentembed_destroydocument) to avoid memory leakage.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| const char *srcFilePath | Source file path.|
| size_t length | Length of the source file path string, excluding the terminator.|
| bool isLinking | Whether to create an OE document in link mode. true: The OE document is created in link mode. When the server edits the OE document, the source file is also modified.<br>                  false: The OE document is created in embedded mode. When the server edits the OE document in response to a client request, a temporary file is copied to the sandbox directory of the client app.|
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) **document | Output parameter. This pointer points to the newly created OE document object.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The following error codes are returned:<br>     CE_ERR_OK: indicates that the operation is successful.<br>     CE_ERR_PARAM_INVALID: indicates that the parameter check fails.<br>     CE_ERR_NULL_POINTER: indicates that a null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: indicates that the device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: indicates that the operation is not supported because the application is in the DLP sandbox.<br>     CE_ERR_INVALID_LINKING_PATH: indicates that the link file is in the app sandbox and the link cannot be created.|

### OH_ContentEmbed_LoadDocumentFromFile()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_LoadDocumentFromFile(const char *srcFilePath, size_t length, ContentEmbed_Document **document)
```

**Description**

Loads an [ContentEmbed_Document](capi-contentembed-contentembed-document.md) instance using an existing file in the OE format.<br> You can destroy the instance using [OH_ContentEmbed_DestroyDocument](capi-content-embed-document-h.md#oh_contentembed_destroydocument) to avoid memory leaks.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| const char *srcFilePath | Source file path, which points to the file to be loaded in the OE format.|
| size_t length | Length of the source file path string, excluding the terminator.|
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) **document | Output parameter. This pointer points to the newly created OE document object.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The following error codes are returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Parameter check failed.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Document_Read()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Document_Read(uint8_t *buffer, size_t length, ContentEmbed_Document *document, size_t offset, size_t *readSize)
```

**Description**

Reads the original binary data from the specified offset position of the OE document object to the buffer.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| uint8_t *buffer | Output parameter. Buffer for storing the data read from the OE document.|
| size_t length | Size of the buffer, in bytes.|
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | Pointer to the OE document object.|
| size_t offset | Offset position from which the data is read in the OE document, starting from 0.|
| size_t *readSize | Output parameter. Length of the actually read data, in bytes.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Parameter check failed.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_STORAGE_OPERATION_FAILED: Operations related to the OE file directory failed.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Document_GetOEid()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Document_GetOEid(const ContentEmbed_Document *document, char *oeid)
```

**Description**

Obtains the identifier OEID from the OE document object.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [const ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | Pointer to the OE document object.|
| char *oeid | Output parameter. Character array for storing the OEID value. The recommended array length is [MAX_OEID_LENGTH](capi-content-embed-common-h.md#macros).|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: The parameter check fails.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Document_IsLinking()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Document_IsLinking(const ContentEmbed_Document *document, bool *isLinking)
```

**Description**

Checks whether an OE document is created in link mode.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [const ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | Pointer to the OE document object.|
| bool *isLinking | Output parameter. true indicates that the OE document is created in link mode. false indicates that the OE document is created in embedded mode.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The following error codes are returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Parameter check failed.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Document_GetNativeFilePath()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Document_GetNativeFilePath(const ContentEmbed_Document *document, char *nativeFilePath)
```

**Description**

Obtains the embedded source file path stored in the client sandbox directory from the OE document.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [const ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | Pointer to the OE document object.|
| char *nativeFilePath | Output parameter. Character array for storing the source file path. It is recommended that the array length be [MAX_PATH_LENGTH](#macros).|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The following error codes are returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Parameter check failed.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Document_GetRootStorage()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Document_GetRootStorage(ContentEmbed_Document *document, ContentEmbed_Storage **storage)
```

**Description**

Obtains the root [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) object from an OpenHarmony document object.<br> You can destroy the instance using [OH_ContentEmbed_DestroyStorage](capi-content-embed-document-h.md#oh_contentembed_destroystorage) to avoid memory leaks.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | Pointer to the OpenHarmony document object.|
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) **storage | Output parameter. After the API is successfully called, this pointer points to the root storage object of the OpenHarmony document.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Result code:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameters.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: The operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Document_Flush()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Document_Flush(const ContentEmbed_Document *document)
```

**Description**

Flushes data in an OpenHarmony document to an OpenHarmony file.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [const ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | Pointer to the OE document object.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The specific error code is returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_FILE_OPERATION_FAILED: Failed to perform the file operation.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Storage_CreateStorage()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_CreateStorage(const ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Storage **childStorage)
```

**Description**

Creates a child [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) object based on the parent storage object and name of the OE document.<br> You can destroy the instance using [OH_ContentEmbed_DestroyStorage](capi-content-embed-document-h.md#oh_contentembed_destroystorage) to avoid memory leaks.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [const ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *parentStorage | Pointer to the parent storage object of the OE document.<br>                      To delete a specified child storage object from the parent storage object, call [OH_ContentEmbed_Storage_DeleteEntry](capi-content-embed-document-h.md#oh_contentembed_storage_deleteentry).<br>                      To delete all child storage objects from the parent storage object, call [OH_ContentEmbed_Storage_DeleteAllEntry](capi-content-embed-document-h.md#oh_contentembed_storage_deleteallentry).|
| const char *name | Name of the child storage object to be created. The value cannot be an empty string. It can contain a maximum of 31 characters and cannot contain invalid characters, such as '/', '\', ':', and '!'.|
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) **childStorage | Output parameter. After the function is successfully called, the pointer points to the newly created child storage object of the OpenEuler document.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The specific error code is returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: The parameter check fails. The possible cause is that the parentStorage or name is invalid.<br>     CE_ERR_NULL_POINTER: The returned pointer is null. The possible cause is that the childStorage fails to be created.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_STORAGE_OPERATION_FAILED: The storage operation fails. The possible cause is that the disk space is insufficient.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Storage_GetStorage()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetStorage(const ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Storage **childStorage)
```

**Description**

Obtains the child [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) object from the parent Storage object and name of the OE document.<br> You can destroy the instance by calling [OH_ContentEmbed_DestroyStorage](capi-content-embed-document-h.md#oh_contentembed_destroystorage) to avoid memory leaks.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [const ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *parentStorage | Pointer to the parent Storage object of the OE document.|
| const char *name | Name of the child Storage object to be obtained. The value cannot be an empty string. It can contain a maximum of 31 characters and cannot contain invalid characters such as '/', '\', ':', and '!'.|
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) **childStorage | Output parameter. After the API is successfully called, the pointer points to the found child Storage object of the OE document.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The specific error code is returned:<br>     CE_ERR_OK: indicates that the operation is successful.<br>     CE_ERR_PARAM_INVALID: indicates that the parameter check fails.<br>     CE_ERR_NULL_POINTER: indicates that a null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: indicates that the device is not supported.<br>     CE_ERR_STORAGE_OPERATION_FAILED: indicates that the operation related to the directory of the OE document fails.<br>     CE_ERR_IN_DLP_SANDBOX: The application is in the DLP sandbox and this operation is not supported.|

### OH_ContentEmbed_Storage_CreateStream()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_CreateStream(ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Stream **childStream)
```

**Description**

Creates a [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) object for the parent storage object and name of an OE document.<br> You can destroy the instance using [OH_ContentEmbed_DestroyStream](capi-content-embed-document-h.md#oh_contentembed_destroystream) to avoid memory leaks.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *parentStorage | Pointer to the parent storage object of an OE document.<br>                      You can call [OH_ContentEmbed_Storage_DeleteEntry](capi-content-embed-document-h.md#oh_contentembed_storage_deleteentry) to delete a specified child stream object from the parent storage object.<br>                      You can call [OH_ContentEmbed_Storage_DeleteAllEntry](capi-content-embed-document-h.md#oh_contentembed_storage_deleteallentry) to delete all child stream objects from the parent storage object.|
| const char *name | Name of the stream to be created, which is used to identify and search for the stream. The value cannot be an empty string. It can contain a maximum of 31 characters and cannot contain invalid characters, such as '/', '\', ':', and '!'.|
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) **childStream | Output parameter. After the call is successful, the pointer points to the newly created stream object of the OE document.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The specific error code is returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_STORAGE_OPERATION_FAILED: Operations related to the directory of the OE document failed.<br>     CE_ERR_STREAM_OPERATION_FAILED: Operations related to the stream of the OE document failed.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Storage_GetStream()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetStream(ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Stream **childStream)
```

**Description**

Obtains the child [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) object from the parent storage object and name of the OE document.<br> You can destroy the instance using [OH_ContentEmbed_DestroyStream](capi-content-embed-document-h.md#oh_contentembed_destroystream) to avoid memory leaks.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *parentStorage | Pointer to the parent storage object of the OE document.|
| const char *name | Name of the stream object of the OE document to be obtained. The parameter cannot be an empty string. The name can contain a maximum of 31 characters and cannot contain invalid characters, such as '/', '\', ':', and '!'.|
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) **childStream | Output parameter. After the call succeeds, the pointer points to the found stream object of the OE document.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: The parameter check fails.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_STORAGE_OPERATION_FAILED: Operations related to the directory of the OE document fail.<br>     CE_ERR_STREAM_OPERATION_FAILED: Operations related to the stream of the OE document fail.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Storage_DeleteEntry()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_DeleteEntry(ContentEmbed_Storage *parentStorage, const char *name)
```

**Description**

Deletes a child storage object or stream object with a specified name from the parent storage object of the OE document.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *parentStorage | Pointer to the parent storage object of the OE document.|
| const char *name | Name of the child storage object or stream object to be deleted. The parameter cannot be an empty string. The name can contain a maximum of 31 characters and cannot contain invalid characters, such as '/', '\', ':', and '!'.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The following error codes are returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_STORAGE_OPERATION_FAILED: Operations related to the directory of the OE file failed.<br>     CE_ERR_FILE_OPERATION_FAILED: Operations on the OE file failed.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Storage_DeleteAllEntry()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_DeleteAllEntry(ContentEmbed_Storage *storage)
```

**Description**

Deletes all entries from the storage object of an OpenEuler document, including the sub-storage objects and sub-stream objects.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *storage | Pointer to the storage object of an OpenEuler document.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The following error codes are returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_STORAGE_OPERATION_FAILED: Operations related to the directory of the OE file failed.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_DestroyStorage()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_DestroyStorage(ContentEmbed_Storage *storage)
```

**Description**

Destroys the [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) object instance of an OpenHarmony document and reclaims the memory.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *storage | Pointer to the storage object of an OpenHarmony document.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The specific error code is returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Stream_Read()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Stream_Read(ContentEmbed_Stream *stream, unsigned char **buffer, size_t length, size_t *num)
```

**Description**

Reads data of a specified length from the current position of the stream object of an OpenHarmony document to the buffer. After the data is successfully read, the offset of the stream object increases by the number of actually read bytes.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) *stream | Pointer to the stream object of an OpenHarmony document.|
| unsigned char **buffer | Output parameter. Pointer to the buffer for storing the read data. The memory is allocated internally in the function. The caller needs to release the memory.|
| size_t length | Maximum number of bytes of data to be read.|
| size_t *num | Output parameter. Number of actually read data items, in bytes.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The following error codes are returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_STREAM_OPERATION_FAILED: Failed to perform the stream operation.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Stream_Write()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Stream_Write(ContentEmbed_Stream *stream, const unsigned char *data, size_t length, size_t *num)
```

**Description**

Writes data of a specified length from the buffer to the current position of the stream object in the OE document. After the data is successfully written, the offset of the stream object increases by the number of actually written bytes.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) *stream | Pointer to the stream object in the OE document.|
| const unsigned char *data | Input parameter. Pointer to the buffer where data is to be written.|
| size_t length | Number of bytes of data to be written.|
| size_t *num | Output parameter. Number of actually written data items, in bytes.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The following error codes are returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_STREAM_OPERATION_FAILED: The stream operation fails.<br>     CE_ERR_IN_DLP_SANDBOX: The operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Stream_Seek()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Stream_Seek(ContentEmbed_Stream *stream, size_t position)
```

**Description**

Sets the current read location of the stream object in an OE document to the specified offset.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) *stream | Pointer to the stream object in an OE document.|
| size_t position | Offset of the stream object relative to the start position, in bytes. The value starts from 0.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_STREAM_OPERATION_FAILED: Failed to perform operations on the stream object in an OE document.<br>     CE_ERR_IN_DLP_SANDBOX: The operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Stream_GetPosition()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Stream_GetPosition(ContentEmbed_Stream *stream, size_t *position)
```

**Description**

Obtains the current position offset of the stream object in an OpenEuler document.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) *stream | Pointer to the stream object of the OE document.|
| size_t *position | Output parameter. Offset of the stream object relative to the start position, in bytes. The value starts from 0.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returned error code:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_STREAM_OPERATION_FAILED: Operations related to the stream object of the OE document failed.<br>     CE_ERR_FILE_OPERATION_FAILED: The file operation failed.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Stream_GetSize()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Stream_GetSize(ContentEmbed_Stream *stream, size_t *size)
```

**Description**

Obtains the total size of the stream object of the OE document, in bytes.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) *stream | Pointer to the stream object of the OE document.|
| size_t *size | Output parameter. Total size of the stream object of the OE document, in bytes.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returned error code:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_STREAM_OPERATION_FAILED: Operations related to the stream of the OE file failed.<br>     CE_ERR_FILE_OPERATION_FAILED: The file operation failed.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_DestroyStream()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_DestroyStream(ContentEmbed_Stream *stream)
```

**Description**

Destroys the [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) object instance of an OE document and reclaims the memory.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) *stream | Pointer to the stream object of an OE document.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: The parameter check failed.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_DestroyDocument()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_DestroyDocument(ContentEmbed_Document *document)
```

**Description**

Destroys the [ContentEmbed_Document](capi-contentembed-contentembed-document.md) object instance and reclaims the memory.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | Pointer to the OE document object.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The following error codes are returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: The parameter check fails.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Storage_GetOEid()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetOEid(ContentEmbed_Storage *storage, char *oeid, size_t oeidSize)
```

**Description**

Obtains the identifier (OEID) of the storage object of an OE document.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *storage | Pointer to the storage object of an OE document.|
| char *oeid | Output parameter. Character array for storing the identifier OEID. It is recommended that the array length be [MAX_OEID_LENGTH](capi-content-embed-common-h.md#macros).|
| size_t oeidSize | Length of the OEID array, in bytes.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The following error codes are returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: The parameter check fails.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_STORAGE_OPERATION_FAILED: Operations related to the directory of the OE document fail.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: The operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Storage_SetOEid()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_SetOEid(ContentEmbed_Storage *storage, char *oeid, size_t oeidSize)
```

**Description**

Sets the identifier of the storage object in an OE document.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *storage | Pointer to the storage object in an OE document.|
| char *oeid | Character array of the identifier OEID to be set. It is recommended that the array length be [MAX_OEID_LENGTH](capi-content-embed-common-h.md#macros).|
| size_t oeidSize | Length of the OEID array, in bytes.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_STORAGE_OPERATION_FAILED: Failed to perform operations related to the directory of the OE document.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: The operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_StorageElements_Create()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_Create(ContentEmbed_StorageElements **storageElements)
```

**Description**

Creates and initializes a [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) instance.<br> You can destroy the instance using [OH_ContentEmbed_StorageElements_Destroy](capi-content-embed-document-h.md#oh_contentembed_storageelements_destroy) to avoid memory leaks.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) **storageElements | Output parameter. After the call is successful, the pointer points to the [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) instance.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_StorageElements_Destroy()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_Destroy(ContentEmbed_StorageElements *storageElements)
```

**Description**

Destroys a [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) instance and reclaims the memory occupied by it.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) *storageElements | Pointer to the [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) instance.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The specific error code is returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Storage_GetElements()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetElements(const ContentEmbed_Storage *storage, ContentEmbed_StorageElements *storageElements)
```

**Description**

Obtains the element list in the storage object of an OE document.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [const ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *storage | Pointer to the storage object of an OE document.|
| [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) *storageElements | Element list in the storage object of an OE document.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The following error codes are returned:<br>     CE_ERR_OK: indicates that the operation is successful.<br>     CE_ERR_PARAM_INVALID: indicates that the parameter check fails.<br>     CE_ERR_NULL_POINTER: indicates that a null pointer is returned.<br>     CE_ERR_STORAGE_OPERATION_FAILED: indicates that the operation related to the directory of the OE format file fails.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: indicates that the device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: indicates that the operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_StorageElements_GetCount()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_GetCount(const ContentEmbed_StorageElements *storageElements, size_t *count)
```

**Description**

Obtains the number of elements in a [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) instance.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [const ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) *storageElements | Pointer to the [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) instance.|
| size_t *count | Output parameter. Number of elements in the element set.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The following error codes are returned:<br>     CE_ERR_OK: indicates that the operation is successful.<br>     CE_ERR_PARAM_INVALID: indicates that the parameter check fails.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: The operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_StorageElements_GetElement()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_GetElement(const ContentEmbed_StorageElements *storageElements, size_t index, ContentEmbed_StorageElement **storageElement)
```

**Description**

Obtains the element at the specified index position of the [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) instance.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [const ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) *storageElements | Pointer to the [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) instance.|
| size_t index | Index position of the element to be obtained, starting from 0.|
| [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) **storageElement | Output parameter. Pointer to the [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_StorageElement_GetName()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_GetName(const ContentEmbed_StorageElement *storageElement, char *name, size_t nameSize)
```

**Description**

Obtains the name of a [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [const ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) *storageElement | Pointer to the [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance.|
| char *name | Output parameter. Used to store the element name string.|
| size_t nameSize | Size of the name buffer, in bytes.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_StorageElement_GetCTime()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_GetCTime(const ContentEmbed_StorageElement *element, uint64_t *ctime)
```

**Description**

Obtains the creation timestamp of a [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance, in milliseconds.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [const ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) *element | Pointer to the [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance.|
| uint64_t *ctime | Output parameter. Pointer to the creation timestamp of the element, in milliseconds.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_NULL_POINTER: The returned pointer is null.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_StorageElement_GetMTime()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_GetMTime(const ContentEmbed_StorageElement *element, uint64_t *mtime)
```

**Description**

Obtains the last modification timestamp of an [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance, in milliseconds.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [const ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) *element | Pointer to the [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance.|
| uint64_t *mtime | Output parameter. Pointer to the last modification timestamp of the element, in milliseconds.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The specific error code is returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_StorageElement_IsStorage()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_IsStorage(const ContentEmbed_StorageElement *storageElement, bool *isStorage)
```

**Description**

Checks whether the [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance is the storage object of an OE document.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [const ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) *storageElement | Pointer to the [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance.|
| bool *isStorage | Output parameter. The value true indicates that the instance is an OE document storage object, and the value false indicates that it is not.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Specific error codes are returned:<br>     CE_ERR_OK: Operations are successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_StorageElement_IsStream()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_IsStream(const ContentEmbed_StorageElement *element, bool *isStream)
```

**Description**

Checks whether the [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance is an OE document stream object.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [const ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) *element | Pointer to the [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance.|
| bool *isStream | Output parameter. The value true indicates that the object is an OE document stream object, and the value false indicates that the object is not an OE document stream object.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Specific error code:<br>     CE_ERR_OK: Operations are successful.<br>     CE_ERR_PARAM_INVALID: Parameter check failed.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Storage_CopyTo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_CopyTo(ContentEmbed_Storage *srcStorage, ContentEmbed_Storage *destStorage)
```

**Description**

Copies all sub-storage objects and stream objects from the source OE document storage object to the target OE document storage object.

**Since**: 24

**Parameters:**

| Name| Description|
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *srcStorage | Pointer to the source OE document storage object.|
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *destStorage | Pointer to the target OE document storage object.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Specific error code:<br>     CE_ERR_OK: Operations are successful.<br>     CE_ERR_PARAM_INVALID: The parameter check fails.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_STORAGE_OPERATION_FAILED: The storage operation fails.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: The operation is not supported because the application is in the DLP sandbox.|
