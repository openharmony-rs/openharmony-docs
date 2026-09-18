# udmf.h

## Overview

Provides unified data management framework related functions and enumerations.

**Library**: libudmf.so

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Related module**: [UDMF](capi-udmf.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_UdmfData](capi-udmf-oh-udmfdata.md) | OH_UdmfData | Describes the unified data type. |
| [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) | OH_UdmfRecord | Describes the record type in the unified data. |
| [OH_UdmfRecordProvider](capi-udmf-oh-udmfrecordprovider.md) | OH_UdmfRecordProvider | Defines the data provider. |
| [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md) | OH_UdmfProperty | Describes some property parameters of unified data. |
| [OH_Udmf_ProgressInfo](capi-udmf-oh-udmf-progressinfo.md) | OH_Udmf_ProgressInfo | Represents the udmf progress information. |
| [OH_UdmfGetDataParams](capi-udmf-oh-udmfgetdataparams.md) | OH_UdmfGetDataParams | Represents the parameters of udmf get data with progress info. |
| [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md) | OH_UdmfOptions | Describes the optional arguments of data operation |
| [OH_UdmfDataLoadParams](capi-udmf-oh-udmfdataloadparams.md) | OH_UdmfDataLoadParams | Indicates data loading params. |
| [OH_UdmfDataLoadInfo](capi-udmf-oh-udmfdataloadinfo.md) | OH_UdmfDataLoadInfo | Indicates data loading information. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Udmf_Intention](#udmf_intention) | Udmf_Intention | Describe the intention type of the udmf. |
| [Udmf_ShareOption](#udmf_shareoption) | Udmf_ShareOption | Describe intra-device usage range type enumeration. |
| [Udmf_FileConflictOptions](#udmf_fileconflictoptions) | Udmf_FileConflictOptions | Describe the types of file conflict options when getting data from the udmf. |
| [Udmf_ProgressIndicator](#udmf_progressindicator) | Udmf_ProgressIndicator | Describe the types of progress indicator when getting data from the udmf. |
| [Udmf_Visibility](#udmf_visibility) | Udmf_Visibility | Describe the visibility range of data |

### Macro

| Name | Description |
| -- | -- |
| UDMF_KEY_BUFFER_LEN (512) | The key minimum memory space size of Unified Data.<br>**Since**: 12 |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_Udmf_DataProgressListener)(OH_Udmf_ProgressInfo* progressInfo, OH_UdmfData* data)](#oh_udmf_dataprogresslistener) | OH_Udmf_DataProgressListener | Defines the callback function used to return the progress information and data. |
| [typedef OH_UdmfData* (\*OH_Udmf_DataLoadHandler)(OH_UdmfDataLoadInfo* acceptableInfo)](#oh_udmf_dataloadhandler) | OH_Udmf_DataLoadHandler | Indicates the callback function for loading data. |
| [OH_UdmfData* OH_UdmfData_Create()](#oh_udmfdata_create) | - | Creates a pointer to the instance of the [OH_UdmfData](capi-udmf-oh-udmfdata.md). |
| [void OH_UdmfData_Destroy(OH_UdmfData* pThis)](#oh_udmfdata_destroy) | - | Destroy a pointer that points to the [OH_UdmfData](capi-udmf-oh-udmfdata.md) instance. |
| [int OH_UdmfData_AddRecord(OH_UdmfData* pThis, OH_UdmfRecord* record)](#oh_udmfdata_addrecord) | - | Add one {OH_UdmfRecord} record to the [OH_UdmfData](capi-udmf-oh-udmfdata.md) data. |
| [bool OH_UdmfData_HasType(OH_UdmfData* pThis, const char* type)](#oh_udmfdata_hastype) | - | Check whether the type exists in the [OH_UdmfData](capi-udmf-oh-udmfdata.md) data. |
| [char** OH_UdmfData_GetTypes(OH_UdmfData* pThis, unsigned int* count)](#oh_udmfdata_gettypes) | - | Get all types in the [OH_UdmfData](capi-udmf-oh-udmfdata.md) data. |
| [OH_UdmfRecord** OH_UdmfData_GetRecords(OH_UdmfData* pThis, unsigned int* count)](#oh_udmfdata_getrecords) | - | Get all records in the [OH_UdmfData](capi-udmf-oh-udmfdata.md) data. |
| [typedef void (\*UdmfData_Finalize)(void* context)](#udmfdata_finalize) | UdmfData_Finalize | Defines the callback function used free the context. |
| [OH_UdmfRecordProvider* OH_UdmfRecordProvider_Create()](#oh_udmfrecordprovider_create) | - | Creates an [OH_UdmfRecordProvider](capi-udmf-oh-udmfrecordprovider.md) instance. |
| [int OH_UdmfRecordProvider_Destroy(OH_UdmfRecordProvider* provider)](#oh_udmfrecordprovider_destroy) | - | Destroy an [OH_UdmfRecordProvider](capi-udmf-oh-udmfrecordprovider.md) instance. |
| [typedef void* (\*OH_UdmfRecordProvider_GetData)(void* context, const char* type)](#oh_udmfrecordprovider_getdata) | OH_UdmfRecordProvider_GetData | Defines a callback function used to obtain data by type. |
| [int OH_UdmfRecordProvider_SetData(OH_UdmfRecordProvider* provider, void* context, const OH_UdmfRecordProvider_GetData callback, const UdmfData_Finalize finalize)](#oh_udmfrecordprovider_setdata) | - | Sets a callback function to obtain data. |
| [OH_UdmfRecord* OH_UdmfRecord_Create()](#oh_udmfrecord_create) | - | Creates a pointer to the instance of the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md), it's relate with UDS data. |
| [void OH_UdmfRecord_Destroy(OH_UdmfRecord* pThis)](#oh_udmfrecord_destroy) | - | Destroy a pointer that points to an instance of [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md). |
| [int OH_UdmfRecord_AddGeneralEntry(OH_UdmfRecord* pThis, const char* typeId, unsigned char* entry, unsigned int count)](#oh_udmfrecord_addgeneralentry) | - | Add one custom data to the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record. |
| [int OH_UdmfRecord_AddPlainText(OH_UdmfRecord* pThis, OH_UdsPlainText* plainText)](#oh_udmfrecord_addplaintext) | - | Add one {OH_UdsPlainText} data to the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record. |
| [int OH_UdmfRecord_AddHyperlink(OH_UdmfRecord* pThis, OH_UdsHyperlink* hyperlink)](#oh_udmfrecord_addhyperlink) | - | Add one {OH_UdsHyperlink} data to the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record. |
| [int OH_UdmfRecord_AddHtml(OH_UdmfRecord* pThis, OH_UdsHtml* html)](#oh_udmfrecord_addhtml) | - | Add one {OH_UdsHtml} data to the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record. |
| [int OH_UdmfRecord_AddAppItem(OH_UdmfRecord* pThis, OH_UdsAppItem* appItem)](#oh_udmfrecord_addappitem) | - | Add one {OH_UdsAppItem} data to the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record. |
| [int OH_UdmfRecord_AddFileUri(OH_UdmfRecord* pThis, OH_UdsFileUri* fileUri)](#oh_udmfrecord_addfileuri) | - | Add one {OH_UdsFileUri} data to the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record. |
| [int OH_UdmfRecord_AddPixelMap(OH_UdmfRecord* pThis, OH_UdsPixelMap* pixelMap)](#oh_udmfrecord_addpixelmap) | - | Add one {OH_UdsPixelMap} data to the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record. |
| [int OH_UdmfRecord_AddArrayBuffer(OH_UdmfRecord* record, const char* type, OH_UdsArrayBuffer* buffer)](#oh_udmfrecord_addarraybuffer) | - | Add one {@link OH_UdsArrayBuffer} data to the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record. |
| [int OH_UdmfRecord_AddContentForm(OH_UdmfRecord* pThis, OH_UdsContentForm* contentForm)](#oh_udmfrecord_addcontentform) | - | Add one {@link OH_UdsContentForm} data to the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record. |
| [char** OH_UdmfRecord_GetTypes(OH_UdmfRecord* pThis, unsigned int* count)](#oh_udmfrecord_gettypes) | - | Get all types in the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record. |
| [int OH_UdmfRecord_GetGeneralEntry(OH_UdmfRecord* pThis, const char* typeId, unsigned char** entry, unsigned int* count)](#oh_udmfrecord_getgeneralentry) | - | Get one entry data from the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record. |
| [int OH_UdmfRecord_GetPlainText(OH_UdmfRecord* pThis, OH_UdsPlainText* plainText)](#oh_udmfrecord_getplaintext) | - | Get one {OH_UdsPlainText} data from the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record. |
| [int OH_UdmfRecord_GetHyperlink(OH_UdmfRecord* pThis, OH_UdsHyperlink* hyperlink)](#oh_udmfrecord_gethyperlink) | - | Get one {OH_UdsHyperlink} data from the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record. |
| [int OH_UdmfRecord_GetHtml(OH_UdmfRecord* pThis, OH_UdsHtml* html)](#oh_udmfrecord_gethtml) | - | Get one {OH_UdsHtml} data from the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record. |
| [int OH_UdmfRecord_GetAppItem(OH_UdmfRecord* pThis, OH_UdsAppItem* appItem)](#oh_udmfrecord_getappitem) | - | Get one {OH_UdsAppItem} data from the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record. |
| [int OH_UdmfRecord_GetFileUri(OH_UdmfRecord* pThis, OH_UdsFileUri* fileUri)](#oh_udmfrecord_getfileuri) | - | Get one {OH_UdsFileUri} data from the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record. |
| [int OH_UdmfRecord_GetPixelMap(OH_UdmfRecord* pThis, OH_UdsPixelMap* pixelMap)](#oh_udmfrecord_getpixelmap) | - | Get one {OH_UdsPixelMap} data from the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record. |
| [int OH_UdmfRecord_SetProvider(OH_UdmfRecord* pThis, const char* const* types, unsigned int count, OH_UdmfRecordProvider* provider)](#oh_udmfrecord_setprovider) | - | Set the data provider of the types. |
| [int OH_UdmfRecord_GetArrayBuffer(OH_UdmfRecord* record, const char* type, OH_UdsArrayBuffer* buffer)](#oh_udmfrecord_getarraybuffer) | - | Get one {@link OH_UdsArrayBuffer} data from the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record. |
| [int OH_UdmfRecord_GetContentForm(OH_UdmfRecord* pThis, OH_UdsContentForm* contentForm)](#oh_udmfrecord_getcontentform) | - | Get one {@link OH_UdsContentForm} data from the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record. |
| [int OH_UdmfData_GetPrimaryPlainText(OH_UdmfData* data, OH_UdsPlainText* plainText)](#oh_udmfdata_getprimaryplaintext) | - | Get primary {@link OH_UdsPlainText} data from the [OH_UdmfData](capi-udmf-oh-udmfdata.md). |
| [int OH_UdmfData_GetPrimaryHtml(OH_UdmfData* data, OH_UdsHtml* html)](#oh_udmfdata_getprimaryhtml) | - | Get one {@link OH_UdsHtml} data from the [OH_UdmfData](capi-udmf-oh-udmfdata.md). |
| [int OH_UdmfData_GetRecordCount(OH_UdmfData* data)](#oh_udmfdata_getrecordcount) | - | Get the count of [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) in the [OH_UdmfData](capi-udmf-oh-udmfdata.md). |
| [OH_UdmfRecord* OH_UdmfData_GetRecord(OH_UdmfData* data, unsigned int index)](#oh_udmfdata_getrecord) | - | Get the record of the specified index from the [OH_UdmfData](capi-udmf-oh-udmfdata.md). |
| [bool OH_UdmfData_IsLocal(OH_UdmfData* data)](#oh_udmfdata_islocal) | - | Checks whether the UDMF data is from a local device. |
| [OH_UdmfProperty* OH_UdmfProperty_Create(OH_UdmfData* unifiedData)](#oh_udmfproperty_create) | - | Creates a pointer to the instance of the [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md) from a [OH_UdmfData](capi-udmf-oh-udmfdata.md) data. |
| [void OH_UdmfProperty_Destroy(OH_UdmfProperty* pThis)](#oh_udmfproperty_destroy) | - | Destroy a pointer that points to the [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md) instance. |
| [const char* OH_UdmfProperty_GetTag(OH_UdmfProperty* pThis)](#oh_udmfproperty_gettag) | - | Get tag value from the [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md). |
| [int64_t OH_UdmfProperty_GetTimestamp(OH_UdmfProperty* pThis)](#oh_udmfproperty_gettimestamp) | - | Get timestamp value from the [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md). |
| [Udmf_ShareOption OH_UdmfProperty_GetShareOption(OH_UdmfProperty* pThis)](#oh_udmfproperty_getshareoption) | - | Get share option value from the [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md). |
| [int OH_UdmfProperty_GetExtrasIntParam(OH_UdmfProperty* pThis, const char* key, int defaultValue)](#oh_udmfproperty_getextrasintparam) | - | Get integer value by key from the [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md). |
| [const char* OH_UdmfProperty_GetExtrasStringParam(OH_UdmfProperty* pThis, const char* key)](#oh_udmfproperty_getextrasstringparam) | - | Get tag value from the [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md). |
| [int OH_UdmfProperty_SetTag(OH_UdmfProperty* pThis, const char* tag)](#oh_udmfproperty_settag) | - | Set tag value to [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md) . |
| [int OH_UdmfProperty_SetShareOption(OH_UdmfProperty* pThis, Udmf_ShareOption option)](#oh_udmfproperty_setshareoption) | - | Set Udmf_ShareOption value to [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md). |
| [int OH_UdmfProperty_SetExtrasIntParam(OH_UdmfProperty* pThis, const char* key, int param)](#oh_udmfproperty_setextrasintparam) | - | Set extras param to [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md). |
| [int OH_UdmfProperty_SetExtrasStringParam(OH_UdmfProperty* pThis, const char* key, const char* param)](#oh_udmfproperty_setextrasstringparam) | - | Set extras param to [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md). |
| [int OH_UdmfProperty_SetAuthPermission(OH_UdmfProperty* pThis, uint32_t authPolicy)](#oh_udmfproperty_setauthpermission) | - | Set auth permission to the [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md). |
| [OH_UdmfOptions* OH_UdmfOptions_Create()](#oh_udmfoptions_create) | - | Creates a pointer to the instance of the [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md). |
| [void OH_UdmfOptions_Destroy(OH_UdmfOptions* pThis)](#oh_udmfoptions_destroy) | - | Destroy the heap memory pointed to by the pointer of [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md). Note that this function cannot be called repeatedly for the same pointer. |
| [const char* OH_UdmfOptions_GetKey(OH_UdmfOptions* pThis)](#oh_udmfoptions_getkey) | - | Get key from the [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md). |
| [int OH_UdmfOptions_SetKey(OH_UdmfOptions* pThis, const char* key)](#oh_udmfoptions_setkey) | - | Set the key to the [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md). |
| [Udmf_Intention OH_UdmfOptions_GetIntention(OH_UdmfOptions* pThis)](#oh_udmfoptions_getintention) | - | Get intention from the [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md). |
| [int OH_UdmfOptions_SetIntention(OH_UdmfOptions* pThis, Udmf_Intention intention)](#oh_udmfoptions_setintention) | - | Set intention value to [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md). |
| [int OH_UdmfOptions_Reset(OH_UdmfOptions* pThis)](#oh_udmfoptions_reset) | - | Reset [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md) to default. |
| [Udmf_Visibility OH_UdmfOptions_GetVisibility(OH_UdmfOptions* pThis)](#oh_udmfoptions_getvisibility) | - | Get visibility from the [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md). |
| [int OH_UdmfOptions_SetVisibility(OH_UdmfOptions* pThis, Udmf_Visibility visibility)](#oh_udmfoptions_setvisibility) | - | Set visibility value to [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md). |
| [int OH_Udmf_GetUnifiedData(const char* key, Udmf_Intention intention, OH_UdmfData* unifiedData)](#oh_udmf_getunifieddata) | - | Get [OH_UdmfData](capi-udmf-oh-udmfdata.md) data from udmf database. |
| [int OH_Udmf_GetUnifiedDataByOptions(OH_UdmfOptions* options, OH_UdmfData** dataArray, unsigned int* dataSize)](#oh_udmf_getunifieddatabyoptions) | - | Get [OH_UdmfData](capi-udmf-oh-udmfdata.md) data array from udmf database by intention. |
| [int OH_Udmf_SetUnifiedData(Udmf_Intention intention, OH_UdmfData* unifiedData, char* key, unsigned int keyLen)](#oh_udmf_setunifieddata) | - | Set [OH_UdmfData](capi-udmf-oh-udmfdata.md) data to database. |
| [int OH_Udmf_SetUnifiedDataByOptions(OH_UdmfOptions* options, OH_UdmfData* unifiedData, char* key, unsigned int keyLen)](#oh_udmf_setunifieddatabyoptions) | - | Set [OH_UdmfData](capi-udmf-oh-udmfdata.md) data to database with options. |
| [int OH_Udmf_UpdateUnifiedData(OH_UdmfOptions* options, OH_UdmfData* unifiedData)](#oh_udmf_updateunifieddata) | - | Update [OH_UdmfData](capi-udmf-oh-udmfdata.md) data to database with options. |
| [int OH_Udmf_DeleteUnifiedData(OH_UdmfOptions* options, OH_UdmfData** dataArray, unsigned int* dataSize)](#oh_udmf_deleteunifieddata) | - | Delete [OH_UdmfData](capi-udmf-oh-udmfdata.md) data of database with options. |
| [OH_UdmfData* OH_UDMF_GetDataElementAt(OH_UdmfData** dataArray, unsigned int index)](#oh_udmf_getdataelementat) | - | Gets the pointer to the element at the specified index from the input array. |
| [void OH_Udmf_DestroyDataArray(OH_UdmfData** dataArray, unsigned int dataSize)](#oh_udmf_destroydataarray) | - | Destroy data array memory. |
| [int OH_UdmfProgressInfo_GetProgress(OH_Udmf_ProgressInfo* progressInfo)](#oh_udmfprogressinfo_getprogress) | - | Gets the progress from the {@OH_Udmf_ProgressInfo}. |
| [int OH_UdmfProgressInfo_GetStatus(OH_Udmf_ProgressInfo* progressInfo)](#oh_udmfprogressinfo_getstatus) | - | Gets the status from the {@OH_Udmf_ProgressInfo}. |
| [OH_UdmfGetDataParams* OH_UdmfGetDataParams_Create()](#oh_udmfgetdataparams_create) | - | Creates a pointer to the instance of the [OH_UdmfGetDataParams](capi-udmf-oh-udmfgetdataparams.md). |
| [void OH_UdmfGetDataParams_Destroy(OH_UdmfGetDataParams* pThis)](#oh_udmfgetdataparams_destroy) | - | Destroy a pointer that points to an instance of [OH_UdmfGetDataParams](capi-udmf-oh-udmfgetdataparams.md). |
| [void OH_UdmfGetDataParams_SetDestUri(OH_UdmfGetDataParams* params, const char* destUri)](#oh_udmfgetdataparams_setdesturi) | - | Sets the destination uri to the {@OH_UdmfGetDataParams}. |
| [void OH_UdmfGetDataParams_SetFileConflictOptions(OH_UdmfGetDataParams* params, const Udmf_FileConflictOptions options)](#oh_udmfgetdataparams_setfileconflictoptions) | - | Sets the file conflict options to the {@OH_UdmfGetDataParams}. |
| [void OH_UdmfGetDataParams_SetProgressIndicator(OH_UdmfGetDataParams* params, const Udmf_ProgressIndicator progressIndicator)](#oh_udmfgetdataparams_setprogressindicator) | - | Sets the progress indicator to the {@OH_UdmfGetDataParams}. |
| [void OH_UdmfGetDataParams_SetDataProgressListener(OH_UdmfGetDataParams* params, const OH_Udmf_DataProgressListener dataProgressListener)](#oh_udmfgetdataparams_setdataprogresslistener) | - | Sets the progress indicator to the {@OH_UdmfGetDataParams}. |
| [void OH_UdmfGetDataParams_SetAcceptableInfo(OH_UdmfGetDataParams* params, OH_UdmfDataLoadInfo* acceptableInfo)](#oh_udmfgetdataparams_setacceptableinfo) | - | Sets the acceptable info to the {@OH_UdmfGetDataParams}. |
| [OH_UdmfDataLoadParams* OH_UdmfDataLoadParams_Create()](#oh_udmfdataloadparams_create) | - | Creates a pointer to the instance of the [OH_UdmfDataLoadParams](capi-udmf-oh-udmfdataloadparams.md). |
| [void OH_UdmfDataLoadParams_Destroy(OH_UdmfDataLoadParams* pThis)](#oh_udmfdataloadparams_destroy) | - | Destroy a pointer that points to an instance of [OH_UdmfDataLoadParams](capi-udmf-oh-udmfdataloadparams.md). |
| [void OH_UdmfDataLoadParams_SetLoadHandler(OH_UdmfDataLoadParams* params, const OH_Udmf_DataLoadHandler dataLoadHandler)](#oh_udmfdataloadparams_setloadhandler) | - | Sets the data load handler to the {@OH_UdmfDataLoadParams}. |
| [void OH_UdmfDataLoadParams_SetDataLoadInfo(OH_UdmfDataLoadParams* params, OH_UdmfDataLoadInfo* dataLoadInfo)](#oh_udmfdataloadparams_setdataloadinfo) | - | Sets the data load info to the {@OH_UdmfDataLoadParams}. |
| [OH_UdmfDataLoadInfo* OH_UdmfDataLoadInfo_Create()](#oh_udmfdataloadinfo_create) | - | Creates a pointer to the instance of the [OH_UdmfDataLoadInfo](capi-udmf-oh-udmfdataloadinfo.md). |
| [void OH_UdmfDataLoadInfo_Destroy(OH_UdmfDataLoadInfo* dataLoadInfo)](#oh_udmfdataloadinfo_destroy) | - | Destroy the heap memory pointed to by the pointer of [OH_UdmfDataLoadInfo](capi-udmf-oh-udmfdataloadinfo.md). Note that this function cannot be called repeatedly for the same pointer. |
| [char** OH_UdmfDataLoadInfo_GetTypes(OH_UdmfDataLoadInfo* dataLoadInfo, unsigned int* count)](#oh_udmfdataloadinfo_gettypes) | - | Gets the types from the {@OH_UdmfDataLoadInfo}. |
| [void OH_UdmfDataLoadInfo_SetType(OH_UdmfDataLoadInfo* dataLoadInfo, const char* type)](#oh_udmfdataloadinfo_settype) | - | Sets the data load info to the {@OH_UdmfDataLoadInfo}. |
| [int OH_UdmfDataLoadInfo_GetRecordCount(OH_UdmfDataLoadInfo* dataLoadInfo)](#oh_udmfdataloadinfo_getrecordcount) | - | Gets the record count from the {@OH_UdmfDataLoadInfo}. |
| [void OH_UdmfDataLoadInfo_SetRecordCount(OH_UdmfDataLoadInfo* dataLoadInfo, unsigned int recordCount)](#oh_udmfdataloadinfo_setrecordcount) | - | Sets the record count to the {@OH_UdmfDataLoadInfo}. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_Udmf_DataProgressListener)(OH_Udmf_ProgressInfo* progressInfo, OH_UdmfData* data) | Defines the callback function used to return the progress information and data.<br>**Since**: 15 |
| OH_UdmfData* (*OH_Udmf_DataLoadHandler)(OH_UdmfDataLoadInfo* acceptableInfo) | Indicates the callback function for loading data.<br>**Since**: 20 |
| void (*UdmfData_Finalize)(void* context) | Defines the callback function used free the context.<br>**Since**: 13 |
| void* (*OH_UdmfRecordProvider_GetData)(void* context, const char* type) | Defines a callback function used to obtain data by type.<br>**Since**: 13 |

## Enum type description

### Udmf_Intention

```c
enum Udmf_Intention
```

**Description**

Describe the intention type of the udmf.

**Since**: 12

| Enum item | Description |
| -- | -- |
| UDMF_INTENTION_DRAG | The intention is drag. |
| UDMF_INTENTION_PASTEBOARD | The intention is pasteboard. |
| UDMF_INTENTION_DATA_HUB | The intention is data hub.<br>**Since**: 20 |
| UDMF_INTENTION_SYSTEM_SHARE | The intention is system share.<br>**Since**: 20 |
| UDMF_INTENTION_PICKER | The intention is picker.<br>**Since**: 20 |
| UDMF_INTENTION_MENU | The intention is menu.<br>**Since**: 20 |

### Udmf_ShareOption

```c
enum Udmf_ShareOption
```

**Description**

Describe intra-device usage range type enumeration.

**Since**: 12

| Enum item | Description |
| -- | -- |
| SHARE_OPTIONS_INVALID | Invalid share option. |
| SHARE_OPTIONS_IN_APP | Allowed to be used in the same application on this device. |
| SHARE_OPTIONS_CROSS_APP | Allowed to be used in the cross application on this device. |

### Udmf_FileConflictOptions

```c
enum Udmf_FileConflictOptions
```

**Description**

Describe the types of file conflict options when getting data from the udmf.

**Since**: 15

| Enum item | Description |
| -- | -- |
| UDMF_OVERWRITE = 0 | Overwrite when dest uri has file with same name. |
| UDMF_SKIP = 1 | Skip when dest uri has file with same name. |

### Udmf_ProgressIndicator

```c
enum Udmf_ProgressIndicator
```

**Description**

Describe the types of progress indicator when getting data from the udmf.

**Since**: 15

| Enum item | Description |
| -- | -- |
| UDMF_NONE = 0 | Getting data without system default progress indicator. |
| UDMF_DEFAULT = 1 | Getting data with system default progress indicator. |

### Udmf_Visibility

```c
enum Udmf_Visibility
```

**Description**

Describe the visibility range of data

**Since**: 20

| Enum item | Description |
| -- | -- |
| UDMF_ALL | The visibility level that specifies that any hap or native can be obtained. |
| UDMF_OWN_PROCESS | The visibility level that specifies that only data providers can be obtained. |


## Function description

### OH_Udmf_DataProgressListener()

```c
typedef void (*OH_Udmf_DataProgressListener)(OH_Udmf_ProgressInfo* progressInfo, OH_UdmfData* data)
```

**Description**

Defines the callback function used to return the progress information and data.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Udmf_ProgressInfo](capi-udmf-oh-udmf-progressinfo.md)\* progressInfo | The progress information notified to Application. |
| [OH_UdmfData](capi-udmf-oh-udmfdata.md)\* data | Represents the unified data. |

### OH_Udmf_DataLoadHandler()

```c
typedef OH_UdmfData* (*OH_Udmf_DataLoadHandler)(OH_UdmfDataLoadInfo* acceptableInfo)
```

**Description**

Indicates the callback function for loading data.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfDataLoadInfo](capi-udmf-oh-udmfdataloadinfo.md)\* acceptableInfo | Indicates the type and number of data that can be accepted by the receiver. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UdmfData*](capi-udmf-oh-udmfdata.md) | Returns the data to be loaded. |

### OH_UdmfData_Create()

```c
OH_UdmfData* OH_UdmfData_Create()
```

**Description**

Creates a pointer to the instance of the [OH_UdmfData](capi-udmf-oh-udmfdata.md).

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UdmfData*](capi-udmf-oh-udmfdata.md) | If the operation is successful, a pointer to the instance of the [OH_UdmfData](capi-udmf-oh-udmfdata.md)  structure is returned. If the operation is failed, nullptr is returned. |

**Reference**:

OH_UdmfData


### OH_UdmfData_Destroy()

```c
void OH_UdmfData_Destroy(OH_UdmfData* pThis)
```

**Description**

Destroy a pointer that points to the [OH_UdmfData](capi-udmf-oh-udmfdata.md) instance.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfData](capi-udmf-oh-udmfdata.md)* pThis | Represents a pointer to an instance of [OH_UdmfData](capi-udmf-oh-udmfdata.md). |

**Reference**:

OH_UdmfData


### OH_UdmfData_AddRecord()

```c
int OH_UdmfData_AddRecord(OH_UdmfData* pThis, OH_UdmfRecord* record)
```

**Description**

Add one {OH_UdmfRecord} record to the [OH_UdmfData](capi-udmf-oh-udmfdata.md) data.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfData](capi-udmf-oh-udmfdata.md)* pThis | Represents a pointer to an instance of [OH_UdmfData](capi-udmf-oh-udmfdata.md). |
| [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md)* record | Represents a pointer to an instance of [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md). |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args. |

**Reference**:

OH_UdmfData Udmf_ErrCode


### OH_UdmfData_HasType()

```c
bool OH_UdmfData_HasType(OH_UdmfData* pThis, const char* type)
```

**Description**

Check whether the type exists in the [OH_UdmfData](capi-udmf-oh-udmfdata.md) data.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfData](capi-udmf-oh-udmfdata.md)* pThis | Represents a pointer to an instance of [OH_UdmfData](capi-udmf-oh-udmfdata.md). |
| const char* type | Represents a string pointer of the type. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns the status of finding type.          {@code false} is not existed.<br>        {@code true} is existed. |

**Reference**:

OH_UdmfData


### OH_UdmfData_GetTypes()

```c
char** OH_UdmfData_GetTypes(OH_UdmfData* pThis, unsigned int* count)
```

**Description**

Get all types in the [OH_UdmfData](capi-udmf-oh-udmfdata.md) data.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfData](capi-udmf-oh-udmfdata.md)* pThis | Represents a pointer to an instance of [OH_UdmfData](capi-udmf-oh-udmfdata.md). |
| unsigned int* count | Represents the types count that is a output param. |

**Returns**:

| Type | Description |
| -- | -- |
| char** | Returns string array that in [OH_UdmfData](capi-udmf-oh-udmfdata.md) when input parameters valid,  otherwise return nullptr. |

**Reference**:

OH_UdmfData


### OH_UdmfData_GetRecords()

```c
OH_UdmfRecord** OH_UdmfData_GetRecords(OH_UdmfData* pThis, unsigned int* count)
```

**Description**

Get all records in the [OH_UdmfData](capi-udmf-oh-udmfdata.md) data.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfData](capi-udmf-oh-udmfdata.md)* pThis | Represents a pointer to an instance of [OH_UdmfData](capi-udmf-oh-udmfdata.md). |
| unsigned int* count | Represents the records count that is a output param. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UdmfRecord**](capi-udmf-oh-udmfrecord.md) | Returns [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) pointer array when input parameters valid, otherwise return nullptr. |

**Reference**:

OH_UdmfData OH_UdmfRecord


### UdmfData_Finalize()

```c
typedef void (*UdmfData_Finalize)(void* context)
```

**Description**

Defines the callback function used free the context.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| void\* context | Pointer to the context which is to be free. |

### OH_UdmfRecordProvider_Create()

```c
OH_UdmfRecordProvider* OH_UdmfRecordProvider_Create()
```

**Description**

Creates an [OH_UdmfRecordProvider](capi-udmf-oh-udmfrecordprovider.md) instance.

**Since**: 13

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UdmfRecordProvider*](capi-udmf-oh-udmfrecordprovider.md) | Returns the pointer to the [OH_UdmfRecordProvider](capi-udmf-oh-udmfrecordprovider.md) instance created if the operation is successful.  Returns nullptr if the memory is not enough. |

**Reference**:

OH_UdmfRecordProvider


### OH_UdmfRecordProvider_Destroy()

```c
int OH_UdmfRecordProvider_Destroy(OH_UdmfRecordProvider* provider)
```

**Description**

Destroy an [OH_UdmfRecordProvider](capi-udmf-oh-udmfrecordprovider.md) instance.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfRecordProvider](capi-udmf-oh-udmfrecordprovider.md)* provider | Pointer to the [OH_UdmfRecordProvider](capi-udmf-oh-udmfrecordprovider.md) instance to destroy. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. For details, see {@link Udmf_ErrCode}.<br>        Returns {@link UDMF_E_OK} if the operation is successful.<br>        Returns {@link UDMF_E_INVALID_PARAM} if invalid args are detected. |

**Reference**:

OH_UdmfRecordProvider Udmf_ErrCode


### OH_UdmfRecordProvider_GetData()

```c
typedef void* (*OH_UdmfRecordProvider_GetData)(void* context, const char* type)
```

**Description**

Defines a callback function used to obtain data by type.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| void\* context | Pointer to the context set by [OH_UdmfRecordProvider_SetData](capi-udmf-h.md#oh_udmfrecordprovider_setdata). |
| const char\* type | Pointer to the type of data to obtain. For details, see {@link udmf_meta.h}. |

**Returns**:

| Type | Description |
| -- | -- |
| void* | Returns the data content. |

### OH_UdmfRecordProvider_SetData()

```c
int OH_UdmfRecordProvider_SetData(OH_UdmfRecordProvider* provider, void* context, const OH_UdmfRecordProvider_GetData callback, const UdmfData_Finalize finalize)
```

**Description**

Sets a callback function to obtain data.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfRecordProvider](capi-udmf-oh-udmfrecordprovider.md)* provider | Pointer to the [OH_UdmfRecordProvider](capi-udmf-oh-udmfrecordprovider.md) instance. |
| void* context | Pointer to the context set, which is the first parameter in OH_UdmfRecordProvider_GetData. |
| [const OH_UdmfRecordProvider_GetData](capi-udmf-h.md#oh_udmfrecordprovider_getdata) callback | Callback to set. For details, see [OH_UdmfRecordProvider_GetData](capi-udmf-h.md#oh_udmfrecordprovider_getdata). |
| [const UdmfData_Finalize](capi-udmf-h.md#udmfdata_finalize) finalize | Optional callback that can free context when destroy provider. For details, see [UdmfData_Finalize](capi-udmf-h.md#udmfdata_finalize). |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. For details, see {@link Udmf_ErrCode}.<br>        Returns {@link UDMF_E_OK} if the operation is successful.<br>        Returns {@link UDMF_E_INVALID_PARAM} if invalid args are detected. |

**Reference**:

OH_UdmfRecordProvider OH_UdmfRecordProvider_GetData UdmfData_Finalize Udmf_ErrCode


### OH_UdmfRecord_Create()

```c
OH_UdmfRecord* OH_UdmfRecord_Create()
```

**Description**

Creates a pointer to the instance of the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md), it's relate with UDS data.

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UdmfRecord*](capi-udmf-oh-udmfrecord.md) | If the operation is successful, a pointer to the instance of the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md)  structure is returned. If the operation is failed, nullptr is returned. |

**Reference**:

OH_UdmfRecord


### OH_UdmfRecord_Destroy()

```c
void OH_UdmfRecord_Destroy(OH_UdmfRecord* pThis)
```

**Description**

Destroy a pointer that points to an instance of [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md).

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md)* pThis | Represents a pointer to an instance of [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md). |

**Reference**:

OH_UdmfRecord


### OH_UdmfRecord_AddGeneralEntry()

```c
int OH_UdmfRecord_AddGeneralEntry(OH_UdmfRecord* pThis, const char* typeId, unsigned char* entry, unsigned int count)
```

**Description**

Add one custom data to the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md)* pThis | Represents a pointer to an instance of [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md). |
| const char* typeId | Represents record type, reference udmf_meta.h. |
| unsigned char* entry | Represents custom data. |
| unsigned int count | Represents the size of data param. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args. |

**Reference**:

OH_UdmfRecord Udmf_ErrCode


### OH_UdmfRecord_AddPlainText()

```c
int OH_UdmfRecord_AddPlainText(OH_UdmfRecord* pThis, OH_UdsPlainText* plainText)
```

**Description**

Add one {OH_UdsPlainText} data to the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md)* pThis | Represents a pointer to an instance of [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md). |
| OH_UdsPlainText* plainText | Represents a pointer to an instance of {@link OH_UdsPlainText}. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args. |

**Reference**:

OH_UdmfRecord OH_UdsPlainText Udmf_ErrCode


### OH_UdmfRecord_AddHyperlink()

```c
int OH_UdmfRecord_AddHyperlink(OH_UdmfRecord* pThis, OH_UdsHyperlink* hyperlink)
```

**Description**

Add one {OH_UdsHyperlink} data to the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md)* pThis | Represents a pointer to an instance of [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md). |
| OH_UdsHyperlink* hyperlink | Represents a pointer to an instance of {@link OH_UdsHyperlink}. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args. |

**Reference**:

OH_UdmfRecord OH_UdsHyperlink Udmf_ErrCode


### OH_UdmfRecord_AddHtml()

```c
int OH_UdmfRecord_AddHtml(OH_UdmfRecord* pThis, OH_UdsHtml* html)
```

**Description**

Add one {OH_UdsHtml} data to the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md)* pThis | Represents a pointer to an instance of [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md). |
| OH_UdsHtml* html | Represents a pointer to an instance of {@link OH_UdsHtml}. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args. |

**Reference**:

OH_UdmfRecord OH_UdsHtml Udmf_ErrCode


### OH_UdmfRecord_AddAppItem()

```c
int OH_UdmfRecord_AddAppItem(OH_UdmfRecord* pThis, OH_UdsAppItem* appItem)
```

**Description**

Add one {OH_UdsAppItem} data to the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md)* pThis | Represents a pointer to an instance of [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md). |
| OH_UdsAppItem* appItem | Represents a pointer to an instance of {@link OH_UdsAppItem}. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args. |

**Reference**:

OH_UdmfRecord OH_UdsAppItem Udmf_ErrCode


### OH_UdmfRecord_AddFileUri()

```c
int OH_UdmfRecord_AddFileUri(OH_UdmfRecord* pThis, OH_UdsFileUri* fileUri)
```

**Description**

Add one {OH_UdsFileUri} data to the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md)* pThis | Represents a pointer to an instance of [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md). |
| OH_UdsFileUri* fileUri | Represents a pointer to an instance of {@link OH_UdsFileUri}. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args. |

**Reference**:

OH_UdmfRecord OH_UdsFileUri Udmf_ErrCode


### OH_UdmfRecord_AddPixelMap()

```c
int OH_UdmfRecord_AddPixelMap(OH_UdmfRecord* pThis, OH_UdsPixelMap* pixelMap)
```

**Description**

Add one {OH_UdsPixelMap} data to the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md)* pThis | Represents a pointer to an instance of [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md). |
| OH_UdsPixelMap* pixelMap | Represents a pointer to an instance of {@link OH_UdsPixelMap}. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args. |

**Reference**:

OH_UdmfRecord OH_UdsPixelMap Udmf_ErrCode


### OH_UdmfRecord_AddArrayBuffer()

```c
int OH_UdmfRecord_AddArrayBuffer(OH_UdmfRecord* record, const char* type, OH_UdsArrayBuffer* buffer)
```

**Description**

Add one {@link OH_UdsArrayBuffer} data to the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md)* record | Represents a pointer to an instance of [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md). |
| const char* type | Represents record type, reference udmf_meta.h. |
| OH_UdsArrayBuffer* buffer | Represents a pointer to an instance of {@link OH_UdsArrayBuffer}. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args. |

**Reference**:

OH_UdmfRecord OH_UdsArrayBuffer Udmf_ErrCode


### OH_UdmfRecord_AddContentForm()

```c
int OH_UdmfRecord_AddContentForm(OH_UdmfRecord* pThis, OH_UdsContentForm* contentForm)
```

**Description**

Add one {@link OH_UdsContentForm} data to the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record.

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md)* pThis | Represents a pointer to an instance of [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md). |
| OH_UdsContentForm* contentForm | Represents a pointer to an instance of {@link OH_UdsContentForm}. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args. |

**Reference**:

OH_UdmfRecord OH_UdsContentForm Udmf_ErrCode


### OH_UdmfRecord_GetTypes()

```c
char** OH_UdmfRecord_GetTypes(OH_UdmfRecord* pThis, unsigned int* count)
```

**Description**

Get all types in the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md)* pThis | Represents a pointer to an instance of [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md). |
| unsigned int* count | Represents the types count that is a output param. |

**Returns**:

| Type | Description |
| -- | -- |
| char** | Returns string array that in [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) when input parameters valid,  otherwise return nullptr. |

**Reference**:

OH_UdmfRecord


### OH_UdmfRecord_GetGeneralEntry()

```c
int OH_UdmfRecord_GetGeneralEntry(OH_UdmfRecord* pThis, const char* typeId, unsigned char** entry, unsigned int* count)
```

**Description**

Get one entry data from the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md)* pThis | Represents a pointer to an instance of [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md). |
| const char* typeId | Represents record type, reference udmf_meta.h. |
| unsigned char** entry | Represents a pointer to entry data that is a output param. |
| unsigned int* count | Represents the entry data length that is a output param. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args.<br>        {@link UDMF_ERR} Internal data error. |

**Reference**:

OH_UdmfRecord Udmf_ErrCode


### OH_UdmfRecord_GetPlainText()

```c
int OH_UdmfRecord_GetPlainText(OH_UdmfRecord* pThis, OH_UdsPlainText* plainText)
```

**Description**

Get one {OH_UdsPlainText} data from the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md)* pThis | Represents a pointer to an instance of [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md). |
| OH_UdsPlainText* plainText | Represents a pointer to an instance of {@link OH_UdsPlainText}. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args.<br>        {@link UDMF_ERR} Internal data error. |

**Reference**:

OH_UdmfRecord OH_UdsPlainText Udmf_ErrCode


### OH_UdmfRecord_GetHyperlink()

```c
int OH_UdmfRecord_GetHyperlink(OH_UdmfRecord* pThis, OH_UdsHyperlink* hyperlink)
```

**Description**

Get one {OH_UdsHyperlink} data from the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md)* pThis | Represents a pointer to an instance of [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md). |
| OH_UdsHyperlink* hyperlink | Represents a pointer to an instance of {@link OH_UdsHyperlink}. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args.<br>        {@link UDMF_ERR} Internal data error. |

**Reference**:

OH_UdmfRecord OH_UdsHyperlink Udmf_ErrCode


### OH_UdmfRecord_GetHtml()

```c
int OH_UdmfRecord_GetHtml(OH_UdmfRecord* pThis, OH_UdsHtml* html)
```

**Description**

Get one {OH_UdsHtml} data from the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md)* pThis | Represents a pointer to an instance of [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md). |
| OH_UdsHtml* html | Represents a pointer to an instance of {@link OH_UdsHtml}. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args.<br>        {@link UDMF_ERR} Internal data error. |

**Reference**:

OH_UdmfRecord OH_UdsHtml Udmf_ErrCode


### OH_UdmfRecord_GetAppItem()

```c
int OH_UdmfRecord_GetAppItem(OH_UdmfRecord* pThis, OH_UdsAppItem* appItem)
```

**Description**

Get one {OH_UdsAppItem} data from the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md)* pThis | Represents a pointer to an instance of [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md). |
| OH_UdsAppItem* appItem | Represents a pointer to an instance of {@link OH_UdsAppItem}. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args.<br>        {@link UDMF_ERR} Internal data error. |

**Reference**:

OH_UdmfRecord OH_UdsAppItem Udmf_ErrCode


### OH_UdmfRecord_GetFileUri()

```c
int OH_UdmfRecord_GetFileUri(OH_UdmfRecord* pThis, OH_UdsFileUri* fileUri)
```

**Description**

Get one {OH_UdsFileUri} data from the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md)* pThis | Represents a pointer to an instance of [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md). |
| OH_UdsFileUri* fileUri | Represents a pointer to an instance of {@link OH_UdsFileUri}. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args. |

**Reference**:

OH_UdmfRecord OH_UdsFileUri Udmf_ErrCode


### OH_UdmfRecord_GetPixelMap()

```c
int OH_UdmfRecord_GetPixelMap(OH_UdmfRecord* pThis, OH_UdsPixelMap* pixelMap)
```

**Description**

Get one {OH_UdsPixelMap} data from the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md)* pThis | Represents a pointer to an instance of [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md). |
| OH_UdsPixelMap* pixelMap | Represents a pointer to an instance of {@link OH_UdsPixelMap}. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args. |

**Reference**:

OH_UdmfRecord OH_UdsPixelMap Udmf_ErrCode


### OH_UdmfRecord_SetProvider()

```c
int OH_UdmfRecord_SetProvider(OH_UdmfRecord* pThis, const char* const* types, unsigned int count, OH_UdmfRecordProvider* provider)
```

**Description**

Set the data provider of the types.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md)* pThis | Represents a pointer to an instance of [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md). |
| const char* const* types | Represents a pointer to a group of data types; |
| unsigned int count | Represents the number of data types; |
| [OH_UdmfRecordProvider](capi-udmf-oh-udmfrecordprovider.md)* provider | Represents a pointer an instance of [OH_UdmfRecordProvider](capi-udmf-oh-udmfrecordprovider.md). |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args. |

**Reference**:

OH_UdmfRecord OH_UdmfRecordProvider Udmf_ErrCode


### OH_UdmfRecord_GetArrayBuffer()

```c
int OH_UdmfRecord_GetArrayBuffer(OH_UdmfRecord* record, const char* type, OH_UdsArrayBuffer* buffer)
```

**Description**

Get one {@link OH_UdsArrayBuffer} data from the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md)* record | Represents a pointer to an instance of [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md). |
| const char* type | Represents record type, reference udmf_meta.h. |
| OH_UdsArrayBuffer* buffer | Represents a pointer to an instance of {@link OH_UdsArrayBuffer}. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args. |

**Reference**:

OH_UdmfRecord OH_UdsArrayBuffer Udmf_ErrCode


### OH_UdmfRecord_GetContentForm()

```c
int OH_UdmfRecord_GetContentForm(OH_UdmfRecord* pThis, OH_UdsContentForm* contentForm)
```

**Description**

Get one {@link OH_UdsContentForm} data from the [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) record.

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md)* pThis | Represents a pointer to an instance of [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md). |
| OH_UdsContentForm* contentForm | Represents a pointer to an instance of {@link OH_UdsContentForm}. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args. |

**Reference**:

OH_UdmfRecord OH_UdsContentForm Udmf_ErrCode


### OH_UdmfData_GetPrimaryPlainText()

```c
int OH_UdmfData_GetPrimaryPlainText(OH_UdmfData* data, OH_UdsPlainText* plainText)
```

**Description**

Get primary {@link OH_UdsPlainText} data from the [OH_UdmfData](capi-udmf-oh-udmfdata.md).

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfData](capi-udmf-oh-udmfdata.md)* data | Represents a pointer to an instance of [OH_UdmfData](capi-udmf-oh-udmfdata.md). |
| OH_UdsPlainText* plainText | Represents a pointer to an instance of {@link OH_UdsPlainText}. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args. |

**Reference**:

OH_UdmfData OH_UdsPlainText Udmf_ErrCode


### OH_UdmfData_GetPrimaryHtml()

```c
int OH_UdmfData_GetPrimaryHtml(OH_UdmfData* data, OH_UdsHtml* html)
```

**Description**

Get one {@link OH_UdsHtml} data from the [OH_UdmfData](capi-udmf-oh-udmfdata.md).

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfData](capi-udmf-oh-udmfdata.md)* data | Represents a pointer to an instance of [OH_UdmfData](capi-udmf-oh-udmfdata.md). |
| OH_UdsHtml* html | Represents a pointer to an instance of {@link OH_UdsHtml}. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args. |

**Reference**:

OH_UdmfData OH_UdsHtml Udmf_ErrCode


### OH_UdmfData_GetRecordCount()

```c
int OH_UdmfData_GetRecordCount(OH_UdmfData* data)
```

**Description**

Get the count of [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) in the [OH_UdmfData](capi-udmf-oh-udmfdata.md).

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfData](capi-udmf-oh-udmfdata.md)* data | Represents a pointer to an instance of [OH_UdmfData](capi-udmf-oh-udmfdata.md). |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the count of [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) |

**Reference**:

OH_UdmfData


### OH_UdmfData_GetRecord()

```c
OH_UdmfRecord* OH_UdmfData_GetRecord(OH_UdmfData* data, unsigned int index)
```

**Description**

Get the record of the specified index from the [OH_UdmfData](capi-udmf-oh-udmfdata.md).

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfData](capi-udmf-oh-udmfdata.md)* data | Represents a pointer to an instance of [OH_UdmfData](capi-udmf-oh-udmfdata.md). |
| unsigned int index | Represents the index of [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) in the [OH_UdmfData](capi-udmf-oh-udmfdata.md). |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UdmfRecord*](capi-udmf-oh-udmfrecord.md) | Returns [OH_UdmfRecord](capi-udmf-oh-udmfrecord.md) pointer when input parameters valid, otherwise return nullptr. |

**Reference**:

OH_UdmfData


### OH_UdmfData_IsLocal()

```c
bool OH_UdmfData_IsLocal(OH_UdmfData* data)
```

**Description**

Checks whether the UDMF data is from a local device.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfData](capi-udmf-oh-udmfdata.md)* data | Represents a pointer to an instance of [OH_UdmfData](capi-udmf-oh-udmfdata.md). |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns a boolean value, which indicates whether the UDMF data is from a local device.          The value {@code true} means the data is from a local device.<br>        The value {@code false} means the opposite. |

**Reference**:

OH_UdmfData


### OH_UdmfProperty_Create()

```c
OH_UdmfProperty* OH_UdmfProperty_Create(OH_UdmfData* unifiedData)
```

**Description**

Creates a pointer to the instance of the [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md) from a [OH_UdmfData](capi-udmf-oh-udmfdata.md) data.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfData](capi-udmf-oh-udmfdata.md)* unifiedData | Represents a pointer to an instance of [OH_UdmfData](capi-udmf-oh-udmfdata.md). |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UdmfProperty*](capi-udmf-oh-udmfproperty.md) | If the operation is successful, a pointer to the instance of the [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md)  structure is returned. If the operation is failed, nullptr is returned. |

**Reference**:

OH_UdmfData OH_UdmfProperty


### OH_UdmfProperty_Destroy()

```c
void OH_UdmfProperty_Destroy(OH_UdmfProperty* pThis)
```

**Description**

Destroy a pointer that points to the [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md) instance.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md)* pThis | Represents a pointer to an instance of [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md). |

**Reference**:

OH_UdmfProperty


### OH_UdmfProperty_GetTag()

```c
const char* OH_UdmfProperty_GetTag(OH_UdmfProperty* pThis)
```

**Description**

Get tag value from the [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md).

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md)* pThis | Represents a pointer to an instance of [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a pointer of the tag value string when input parameters valid, otherwise return nullptr. |

**Reference**:

OH_UdmfProperty


### OH_UdmfProperty_GetTimestamp()

```c
int64_t OH_UdmfProperty_GetTimestamp(OH_UdmfProperty* pThis)
```

**Description**

Get timestamp value from the [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md).

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md)* pThis | Represents a pointer to an instance of [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md). |

**Returns**:

| Type | Description |
| -- | -- |
| int64_t | Returns timestamp value. |

**Reference**:

[OH_UdmfProperty](capi-udmf-oh-udmfproperty.md)


### OH_UdmfProperty_GetShareOption()

```c
Udmf_ShareOption OH_UdmfProperty_GetShareOption(OH_UdmfProperty* pThis)
```

**Description**

Get share option value from the [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md).

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md)* pThis | Represents a pointer to an instance of [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md). |

**Returns**:

| Type | Description |
| -- | -- |
| [Udmf_ShareOption](capi-udmf-h.md#udmf_shareoption) | Returns [Udmf_ShareOption](capi-udmf-h.md#udmf_shareoption) value. |

**Reference**:

OH_UdmfProperty Udmf_ShareOption


### OH_UdmfProperty_GetExtrasIntParam()

```c
int OH_UdmfProperty_GetExtrasIntParam(OH_UdmfProperty* pThis, const char* key, int defaultValue)
```

**Description**

Get integer value by key from the [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md).

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md)* pThis | Represents a pointer to an instance of [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md). |
| const char* key | Represents key-value pair's key |
| int defaultValue | Represents when get value failure. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns value associated with the key in successfully, otherwise return defaultValue. |

**Reference**:

OH_UdmfProperty


### OH_UdmfProperty_GetExtrasStringParam()

```c
const char* OH_UdmfProperty_GetExtrasStringParam(OH_UdmfProperty* pThis, const char* key)
```

**Description**

Get tag value from the [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md).

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md)* pThis | Represents a pointer to an instance of [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md). |
| const char* key | Represents key-value pair's key. |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a pointer of the key value string when input parameters valid, otherwise return nullptr. |

**Reference**:

[OH_UdmfProperty](capi-udmf-oh-udmfproperty.md)


### OH_UdmfProperty_SetTag()

```c
int OH_UdmfProperty_SetTag(OH_UdmfProperty* pThis, const char* tag)
```

**Description**

Set tag value to [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md) .

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md)* pThis | Represents a pointer to an instance of [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md). |
| const char* tag | Represents new tag param. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args. |

**Reference**:

OH_UdmfProperty Udmf_ErrCode


### OH_UdmfProperty_SetShareOption()

```c
int OH_UdmfProperty_SetShareOption(OH_UdmfProperty* pThis, Udmf_ShareOption option)
```

**Description**

Set Udmf_ShareOption value to [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md).

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md)* pThis | Represents a pointer to an instance of [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md). |
| [Udmf_ShareOption](capi-udmf-h.md#udmf_shareoption) option | Represents new [Udmf_ShareOption](capi-udmf-h.md#udmf_shareoption) param. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args. |

**Reference**:

OH_UdmfProperty Udmf_ShareOption Udmf_ErrCode


### OH_UdmfProperty_SetExtrasIntParam()

```c
int OH_UdmfProperty_SetExtrasIntParam(OH_UdmfProperty* pThis, const char* key, int param)
```

**Description**

Set extras param to [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md).

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md)* pThis | Represents a pointer to an instance of [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md). |
| const char* key | Represents extras param's key value. |
| int param | Represents value of k-v pairs. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args. |

**Reference**:

OH_UdmfProperty Udmf_ErrCode


### OH_UdmfProperty_SetExtrasStringParam()

```c
int OH_UdmfProperty_SetExtrasStringParam(OH_UdmfProperty* pThis, const char* key, const char* param)
```

**Description**

Set extras param to [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md).

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md)* pThis | Represents a pointer to an instance of [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md). |
| const char* key | Represents extras param's key value. |
| const char* param | Represents value of k-v pairs. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args. |

**Reference**:

OH_UdmfProperty Udmf_ErrCode


### OH_UdmfProperty_SetAuthPermission()

```c
int OH_UdmfProperty_SetAuthPermission(OH_UdmfProperty* pThis, uint32_t authPolicy)
```

**Description**

Set auth permission to the [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md).

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md)* pThis | Represents a pointer to an instance of [OH_UdmfProperty](capi-udmf-oh-udmfproperty.md). |
| uint32_t authPolicy | Represents auth permission. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args. |

**Reference**:

OH_UdmfProperty Udmf_ErrCode


### OH_UdmfOptions_Create()

```c
OH_UdmfOptions* OH_UdmfOptions_Create()
```

**Description**

Creates a pointer to the instance of the [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md).

**Since**: 20

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UdmfOptions*](capi-udmf-oh-udmfoptions.md) | If the operation is successful, a pointer to the instance of the [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md)  structure is returned. If the operation is failed, nullptr is returned. |

**Reference**:

OH_UdmfOptions


### OH_UdmfOptions_Destroy()

```c
void OH_UdmfOptions_Destroy(OH_UdmfOptions* pThis)
```

**Description**

Destroy the heap memory pointed to by the pointer of [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md). Note that this function cannot be called repeatedly for the same pointer.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md)* pThis | Represents a pointer to an instance of [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md). |

**Reference**:

OH_UdmfOptions


### OH_UdmfOptions_GetKey()

```c
const char* OH_UdmfOptions_GetKey(OH_UdmfOptions* pThis)
```

**Description**

Get key from the [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md)* pThis | Represents a pointer to an instance of [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a pointer of the value string when input args normally, otherwise return nullptr. |

**Reference**:

[OH_UdmfOptions](capi-udmf-oh-udmfoptions.md)


### OH_UdmfOptions_SetKey()

```c
int OH_UdmfOptions_SetKey(OH_UdmfOptions* pThis, const char* key)
```

**Description**

Set the key to the [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md)* pThis | Represents a pointer to an instance of [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md). |
| const char* key | Represents a new string value of the key. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args. |

**Reference**:

OH_UdmfOptions Udmf_ErrCode


### OH_UdmfOptions_GetIntention()

```c
Udmf_Intention OH_UdmfOptions_GetIntention(OH_UdmfOptions* pThis)
```

**Description**

Get intention from the [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md)* pThis | Represents a pointer to an instance of [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md). |

**Returns**:

| Type | Description |
| -- | -- |
| [Udmf_Intention](capi-udmf-h.md#udmf_intention) | Returns [Udmf_Intention](capi-udmf-h.md#udmf_intention) value. |

**Reference**:

OH_UdmfOptions Udmf_Intention


### OH_UdmfOptions_SetIntention()

```c
int OH_UdmfOptions_SetIntention(OH_UdmfOptions* pThis, Udmf_Intention intention)
```

**Description**

Set intention value to [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md)* pThis | Represents a pointer to an instance of [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md). |
| [Udmf_Intention](capi-udmf-h.md#udmf_intention) intention | Represents new [Udmf_Intention](capi-udmf-h.md#udmf_intention) param. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args. |

**Reference**:

OH_UdmfOptions Udmf_Intention Udmf_ErrCode


### OH_UdmfOptions_Reset()

```c
int OH_UdmfOptions_Reset(OH_UdmfOptions* pThis)
```

**Description**

Reset [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md) to default.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md)* pThis | Represents a pointer to an instance of [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md). |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args. |

**Reference**:

OH_UdmfOptions Udmf_ErrCode


### OH_UdmfOptions_GetVisibility()

```c
Udmf_Visibility OH_UdmfOptions_GetVisibility(OH_UdmfOptions* pThis)
```

**Description**

Get visibility from the [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md)* pThis | Represents a pointer to an instance of [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md). |

**Returns**:

| Type | Description |
| -- | -- |
| [Udmf_Visibility](capi-udmf-h.md#udmf_visibility) | Returns [Udmf_Visibility](capi-udmf-h.md#udmf_visibility) value. |

**Reference**:

OH_UdmfOptions Udmf_Visibility


### OH_UdmfOptions_SetVisibility()

```c
int OH_UdmfOptions_SetVisibility(OH_UdmfOptions* pThis, Udmf_Visibility visibility)
```

**Description**

Set visibility value to [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md)* pThis | Represents a pointer to an instance of [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md). |
| [Udmf_Visibility](capi-udmf-h.md#udmf_visibility) visibility | Represents new [Udmf_Visibility](capi-udmf-h.md#udmf_visibility) param. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args. |

**Reference**:

OH_UdmfOptions Udmf_Visibility Udmf_ErrCode


### OH_Udmf_GetUnifiedData()

```c
int OH_Udmf_GetUnifiedData(const char* key, Udmf_Intention intention, OH_UdmfData* unifiedData)
```

**Description**

Get [OH_UdmfData](capi-udmf-oh-udmfdata.md) data from udmf database.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* key | Represents database store's key value. |
| [Udmf_Intention](capi-udmf-h.md#udmf_intention) intention | Represents data type [Udmf_Intention](capi-udmf-h.md#udmf_intention) |
| [OH_UdmfData](capi-udmf-oh-udmfdata.md)* unifiedData | Represents output params of [OH_UdmfData](capi-udmf-oh-udmfdata.md); |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args.<br>        {@link UDMF_ERR} Internal data error.              The possible cause is that the server is faulty or the memory is insufficient. |

**Reference**:

OH_UdmfProperty Udmf_Intention Udmf_ErrCode


### OH_Udmf_GetUnifiedDataByOptions()

```c
int OH_Udmf_GetUnifiedDataByOptions(OH_UdmfOptions* options, OH_UdmfData** dataArray, unsigned int* dataSize)
```

**Description**

Get [OH_UdmfData](capi-udmf-oh-udmfdata.md) data array from udmf database by intention.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md)* options | Represents a pointer to an instance of [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md). |
| [OH_UdmfData](capi-udmf-oh-udmfdata.md)** dataArray | Represents output params of [OH_UdmfData](capi-udmf-oh-udmfdata.md). It should be accessed using [OH_UDMF_GetDataElementAt](capi-udmf-h.md#oh_udmf_getdataelementat) to retrieve elements by index. This pointer needs to be released using the [OH_Udmf_DestroyDataArray](capi-udmf-h.md#oh_udmf_destroydataarray) function. |
| unsigned int* dataSize | Represents the data count of output params. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args.<br>        {@link UDMF_ERR} Internal data error.              The possible cause is that the server is faulty or the memory is insufficient. |

**Reference**:

OH_UdmfData Udmf_Intention Udmf_ErrCode


### OH_Udmf_SetUnifiedData()

```c
int OH_Udmf_SetUnifiedData(Udmf_Intention intention, OH_UdmfData* unifiedData, char* key, unsigned int keyLen)
```

**Description**

Set [OH_UdmfData](capi-udmf-oh-udmfdata.md) data to database.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Udmf_Intention](capi-udmf-h.md#udmf_intention) intention | Represents data type [Udmf_Intention](capi-udmf-h.md#udmf_intention). |
| [OH_UdmfData](capi-udmf-oh-udmfdata.md)* unifiedData | Represents a pointer to an instance of [OH_UdmfData](capi-udmf-oh-udmfdata.md). |
| char* key | Represents return value after set data to database successfully, it's memory size not less than {@link UDMF_KEY_BUFFER_LEN}. |
| unsigned int keyLen | Represents size of key param. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args.<br>        {@link UDMF_ERR} Internal data error.              The possible cause is that the server is faulty or the memory is insufficient. |

**Reference**:

OH_UdmfProperty Udmf_Intention Udmf_ErrCode


### OH_Udmf_SetUnifiedDataByOptions()

```c
int OH_Udmf_SetUnifiedDataByOptions(OH_UdmfOptions* options, OH_UdmfData* unifiedData, char* key, unsigned int keyLen)
```

**Description**

Set [OH_UdmfData](capi-udmf-oh-udmfdata.md) data to database with options.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md)* options | Represents a pointer to an instance of [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md). |
| [OH_UdmfData](capi-udmf-oh-udmfdata.md)* unifiedData | Represents a pointer to an instance of [OH_UdmfData](capi-udmf-oh-udmfdata.md). |
| char* key | Represents return value after set data to database successfully, it's memory size not less than {@link UDMF_KEY_BUFFER_LEN}. |
| unsigned int keyLen | Represents size of key param. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args.<br>        {@link UDMF_ERR} Internal data error.              The possible cause is that the server is faulty or the memory is insufficient. |

**Reference**:

OH_UdmfOptions OH_UdmfData Udmf_ErrCode


### OH_Udmf_UpdateUnifiedData()

```c
int OH_Udmf_UpdateUnifiedData(OH_UdmfOptions* options, OH_UdmfData* unifiedData)
```

**Description**

Update [OH_UdmfData](capi-udmf-oh-udmfdata.md) data to database with options.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md)* options | Represents a pointer to an instance of [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md). |
| [OH_UdmfData](capi-udmf-oh-udmfdata.md)* unifiedData | Represents a pointer to an instance of [OH_UdmfData](capi-udmf-oh-udmfdata.md). |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args.<br>        {@link UDMF_ERR} Internal data error.              The possible cause is that the server is faulty or the memory is insufficient. |

**Reference**:

OH_UdmfOptions OH_UdmfData Udmf_ErrCode


### OH_Udmf_DeleteUnifiedData()

```c
int OH_Udmf_DeleteUnifiedData(OH_UdmfOptions* options, OH_UdmfData** dataArray, unsigned int* dataSize)
```

**Description**

Delete [OH_UdmfData](capi-udmf-oh-udmfdata.md) data of database with options.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md)* options | Represents a pointer to an instance of [OH_UdmfOptions](capi-udmf-oh-udmfoptions.md). |
| [OH_UdmfData](capi-udmf-oh-udmfdata.md)** dataArray | Represents output params of [OH_UdmfData](capi-udmf-oh-udmfdata.md). It should be accessed using [OH_UDMF_GetDataElementAt](capi-udmf-h.md#oh_udmf_getdataelementat) to retrieve elements by index. This pointer needs to be released using the [OH_Udmf_DestroyDataArray](capi-udmf-h.md#oh_udmf_destroydataarray) function. |
| unsigned int* dataSize | Represents the data count of output params. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link Udmf_ErrCode}.<br>        {@link UDMF_E_OK} success.<br>        {@link UDMF_E_INVALID_PARAM} The error code for common invalid args.<br>        {@link UDMF_ERR} Internal data error.              The possible cause is that the server is faulty or the memory is insufficient. |

**Reference**:

OH_UdmfData Udmf_Intention Udmf_ErrCode


### OH_UDMF_GetDataElementAt()

```c
OH_UdmfData* OH_UDMF_GetDataElementAt(OH_UdmfData** dataArray, unsigned int index)
```

**Description**

Gets the pointer to the element at the specified index from the input array.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfData](capi-udmf-oh-udmfdata.md)** dataArray | A pointer to an array of [OH_UdmfData](capi-udmf-oh-udmfdata.md) pointers. |
| unsigned int index | The index of the desired element. Note that the input index should not exceed the array range. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UdmfData*](capi-udmf-oh-udmfdata.md) | A pointer to the [OH_UdmfData](capi-udmf-oh-udmfdata.md) element at the specified index; returns NULL if the array is NULL. |

**Reference**:

[OH_UdmfData](capi-udmf-oh-udmfdata.md)


### OH_Udmf_DestroyDataArray()

```c
void OH_Udmf_DestroyDataArray(OH_UdmfData** dataArray, unsigned int dataSize)
```

**Description**

Destroy data array memory.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfData](capi-udmf-oh-udmfdata.md)** dataArray | Represents a point to [OH_UdmfData](capi-udmf-oh-udmfdata.md). |
| unsigned int dataSize | Represents data size in list. |

**Reference**:

[OH_UdmfData](capi-udmf-oh-udmfdata.md)


### OH_UdmfProgressInfo_GetProgress()

```c
int OH_UdmfProgressInfo_GetProgress(OH_Udmf_ProgressInfo* progressInfo)
```

**Description**

Gets the progress from the {@OH_Udmf_ProgressInfo}.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Udmf_ProgressInfo](capi-udmf-oh-udmf-progressinfo.md)* progressInfo | Represents a pointer to an instance of [OH_Udmf_ProgressInfo](capi-udmf-oh-udmf-progressinfo.md). |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the progress. |

**Reference**:

[OH_Udmf_ProgressInfo](capi-udmf-oh-udmf-progressinfo.md)


### OH_UdmfProgressInfo_GetStatus()

```c
int OH_UdmfProgressInfo_GetStatus(OH_Udmf_ProgressInfo* progressInfo)
```

**Description**

Gets the status from the {@OH_Udmf_ProgressInfo}.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Udmf_ProgressInfo](capi-udmf-oh-udmf-progressinfo.md)* progressInfo | Represents a pointer to an instance of [OH_Udmf_ProgressInfo](capi-udmf-oh-udmf-progressinfo.md). |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code. See {@link Udmf_ListenerStatus}. |

**Reference**:

OH_Udmf_ProgressInfo Udmf_ListenerStatus


### OH_UdmfGetDataParams_Create()

```c
OH_UdmfGetDataParams* OH_UdmfGetDataParams_Create()
```

**Description**

Creates a pointer to the instance of the [OH_UdmfGetDataParams](capi-udmf-oh-udmfgetdataparams.md).

**Since**: 15

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UdmfGetDataParams*](capi-udmf-oh-udmfgetdataparams.md) | If the operation is successful, a pointer to the instance of the [OH_UdmfGetDataParams](capi-udmf-oh-udmfgetdataparams.md)  structure is returned. If the operation is failed, nullptr is returned. |

**Reference**:

[OH_UdmfGetDataParams](capi-udmf-oh-udmfgetdataparams.md)


### OH_UdmfGetDataParams_Destroy()

```c
void OH_UdmfGetDataParams_Destroy(OH_UdmfGetDataParams* pThis)
```

**Description**

Destroy a pointer that points to an instance of [OH_UdmfGetDataParams](capi-udmf-oh-udmfgetdataparams.md).

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfGetDataParams](capi-udmf-oh-udmfgetdataparams.md)* pThis | Represents a pointer to an instance of [OH_UdmfGetDataParams](capi-udmf-oh-udmfgetdataparams.md). |

**Reference**:

[OH_UdmfGetDataParams](capi-udmf-oh-udmfgetdataparams.md)


### OH_UdmfGetDataParams_SetDestUri()

```c
void OH_UdmfGetDataParams_SetDestUri(OH_UdmfGetDataParams* params, const char* destUri)
```

**Description**

Sets the destination uri to the {@OH_UdmfGetDataParams}.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfGetDataParams](capi-udmf-oh-udmfgetdataparams.md)* params | Represents a pointer to an instance of [OH_UdmfGetDataParams](capi-udmf-oh-udmfgetdataparams.md). |
| const char* destUri | Pointer to a destination uri. |

**Reference**:

[OH_UdmfGetDataParams](capi-udmf-oh-udmfgetdataparams.md)


### OH_UdmfGetDataParams_SetFileConflictOptions()

```c
void OH_UdmfGetDataParams_SetFileConflictOptions(OH_UdmfGetDataParams* params, const Udmf_FileConflictOptions options)
```

**Description**

Sets the file conflict options to the {@OH_UdmfGetDataParams}.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfGetDataParams](capi-udmf-oh-udmfgetdataparams.md)* params | Represents a pointer to an instance of [OH_UdmfGetDataParams](capi-udmf-oh-udmfgetdataparams.md). |
| [const Udmf_FileConflictOptions](capi-udmf-h.md#udmf_fileconflictoptions) options | Represents to the file conflict options. |

**Reference**:

OH_UdmfGetDataParams Udmf_FileConflictOptions


### OH_UdmfGetDataParams_SetProgressIndicator()

```c
void OH_UdmfGetDataParams_SetProgressIndicator(OH_UdmfGetDataParams* params, const Udmf_ProgressIndicator progressIndicator)
```

**Description**

Sets the progress indicator to the {@OH_UdmfGetDataParams}.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfGetDataParams](capi-udmf-oh-udmfgetdataparams.md)* params | Represents a pointer to an instance of [OH_UdmfGetDataParams](capi-udmf-oh-udmfgetdataparams.md). |
| [const Udmf_ProgressIndicator](capi-udmf-h.md#udmf_progressindicator) progressIndicator | Represents to the progress indicator. |

**Reference**:

OH_UdmfGetDataParams Udmf_ProgressIndicator


### OH_UdmfGetDataParams_SetDataProgressListener()

```c
void OH_UdmfGetDataParams_SetDataProgressListener(OH_UdmfGetDataParams* params, const OH_Udmf_DataProgressListener dataProgressListener)
```

**Description**

Sets the progress indicator to the {@OH_UdmfGetDataParams}.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfGetDataParams](capi-udmf-oh-udmfgetdataparams.md)* params | Represents a pointer to an instance of [OH_UdmfGetDataParams](capi-udmf-oh-udmfgetdataparams.md). |
| [const OH_Udmf_DataProgressListener](capi-udmf-h.md#oh_udmf_dataprogresslistener) dataProgressListener | Represents to the data progress listener. |

**Reference**:

OH_UdmfGetDataParams OH_Udmf_DataProgressListener


### OH_UdmfGetDataParams_SetAcceptableInfo()

```c
void OH_UdmfGetDataParams_SetAcceptableInfo(OH_UdmfGetDataParams* params, OH_UdmfDataLoadInfo* acceptableInfo)
```

**Description**

Sets the acceptable info to the {@OH_UdmfGetDataParams}.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfGetDataParams](capi-udmf-oh-udmfgetdataparams.md)* params | Represents a pointer to an instance of [OH_UdmfGetDataParams](capi-udmf-oh-udmfgetdataparams.md). |
| [OH_UdmfDataLoadInfo](capi-udmf-oh-udmfdataloadinfo.md)* acceptableInfo | Represents a pointer to an instance of [OH_UdmfDataLoadInfo](capi-udmf-oh-udmfdataloadinfo.md). |

**Reference**:

OH_UdmfGetDataParams OH_UdmfDataLoadInfo


### OH_UdmfDataLoadParams_Create()

```c
OH_UdmfDataLoadParams* OH_UdmfDataLoadParams_Create()
```

**Description**

Creates a pointer to the instance of the [OH_UdmfDataLoadParams](capi-udmf-oh-udmfdataloadparams.md).

**Since**: 20

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UdmfDataLoadParams*](capi-udmf-oh-udmfdataloadparams.md) | If the operation is successful, a pointer to the instance of the [OH_UdmfDataLoadParams](capi-udmf-oh-udmfdataloadparams.md)  structure is returned. If the operation is failed, nullptr is returned. |

**Reference**:

[OH_UdmfDataLoadParams](capi-udmf-oh-udmfdataloadparams.md)


### OH_UdmfDataLoadParams_Destroy()

```c
void OH_UdmfDataLoadParams_Destroy(OH_UdmfDataLoadParams* pThis)
```

**Description**

Destroy a pointer that points to an instance of [OH_UdmfDataLoadParams](capi-udmf-oh-udmfdataloadparams.md).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfDataLoadParams](capi-udmf-oh-udmfdataloadparams.md)* pThis | Represents a pointer to an instance of [OH_UdmfDataLoadParams](capi-udmf-oh-udmfdataloadparams.md). |

**Reference**:

[OH_UdmfDataLoadParams](capi-udmf-oh-udmfdataloadparams.md)


### OH_UdmfDataLoadParams_SetLoadHandler()

```c
void OH_UdmfDataLoadParams_SetLoadHandler(OH_UdmfDataLoadParams* params, const OH_Udmf_DataLoadHandler dataLoadHandler)
```

**Description**

Sets the data load handler to the {@OH_UdmfDataLoadParams}.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfDataLoadParams](capi-udmf-oh-udmfdataloadparams.md)* params | Represents a pointer to an instance of [OH_UdmfDataLoadParams](capi-udmf-oh-udmfdataloadparams.md). |
| [const OH_Udmf_DataLoadHandler](capi-udmf-h.md#oh_udmf_dataloadhandler) dataLoadHandler | Represents to the data load handler. |

**Reference**:

OH_UdmfDataLoadParams OH_Udmf_DataLoadHandler


### OH_UdmfDataLoadParams_SetDataLoadInfo()

```c
void OH_UdmfDataLoadParams_SetDataLoadInfo(OH_UdmfDataLoadParams* params, OH_UdmfDataLoadInfo* dataLoadInfo)
```

**Description**

Sets the data load info to the {@OH_UdmfDataLoadParams}.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfDataLoadParams](capi-udmf-oh-udmfdataloadparams.md)* params | Represents a pointer to an instance of [OH_UdmfDataLoadParams](capi-udmf-oh-udmfdataloadparams.md). |
| [OH_UdmfDataLoadInfo](capi-udmf-oh-udmfdataloadinfo.md)* dataLoadInfo | Represents a pointer to an instance of [OH_UdmfDataLoadInfo](capi-udmf-oh-udmfdataloadinfo.md). |

**Reference**:

OH_UdmfDataLoadParams OH_UdmfDataLoadInfo


### OH_UdmfDataLoadInfo_Create()

```c
OH_UdmfDataLoadInfo* OH_UdmfDataLoadInfo_Create()
```

**Description**

Creates a pointer to the instance of the [OH_UdmfDataLoadInfo](capi-udmf-oh-udmfdataloadinfo.md).

**Since**: 20

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UdmfDataLoadInfo*](capi-udmf-oh-udmfdataloadinfo.md) | If the operation is successful, a pointer to the instance of the [OH_UdmfDataLoadInfo](capi-udmf-oh-udmfdataloadinfo.md)  structure is returned. If the operation is failed, nullptr is returned. |

**Reference**:

[OH_UdmfDataLoadInfo](capi-udmf-oh-udmfdataloadinfo.md)


### OH_UdmfDataLoadInfo_Destroy()

```c
void OH_UdmfDataLoadInfo_Destroy(OH_UdmfDataLoadInfo* dataLoadInfo)
```

**Description**

Destroy the heap memory pointed to by the pointer of [OH_UdmfDataLoadInfo](capi-udmf-oh-udmfdataloadinfo.md). Note that this function cannot be called repeatedly for the same pointer.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfDataLoadInfo](capi-udmf-oh-udmfdataloadinfo.md)* dataLoadInfo | Represents a pointer to an instance of [OH_UdmfDataLoadInfo](capi-udmf-oh-udmfdataloadinfo.md). |

**Reference**:

[OH_UdmfDataLoadInfo](capi-udmf-oh-udmfdataloadinfo.md)


### OH_UdmfDataLoadInfo_GetTypes()

```c
char** OH_UdmfDataLoadInfo_GetTypes(OH_UdmfDataLoadInfo* dataLoadInfo, unsigned int* count)
```

**Description**

Gets the types from the {@OH_UdmfDataLoadInfo}.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfDataLoadInfo](capi-udmf-oh-udmfdataloadinfo.md)* dataLoadInfo | Represents a pointer to an instance of [OH_UdmfDataLoadInfo](capi-udmf-oh-udmfdataloadinfo.md). |
| unsigned int* count | the types count of data. |

**Returns**:

| Type | Description |
| -- | -- |
| char** | Returns the types of data. |

**Reference**:

[OH_UdmfDataLoadInfo](capi-udmf-oh-udmfdataloadinfo.md)


### OH_UdmfDataLoadInfo_SetType()

```c
void OH_UdmfDataLoadInfo_SetType(OH_UdmfDataLoadInfo* dataLoadInfo, const char* type)
```

**Description**

Sets the data load info to the {@OH_UdmfDataLoadInfo}.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfDataLoadInfo](capi-udmf-oh-udmfdataloadinfo.md)* dataLoadInfo | Represents a pointer to an instance of [OH_UdmfDataLoadInfo](capi-udmf-oh-udmfdataloadinfo.md). |
| const char* type | Represents the type of data. |

**Reference**:

[OH_UdmfDataLoadInfo](capi-udmf-oh-udmfdataloadinfo.md)


### OH_UdmfDataLoadInfo_GetRecordCount()

```c
int OH_UdmfDataLoadInfo_GetRecordCount(OH_UdmfDataLoadInfo* dataLoadInfo)
```

**Description**

Gets the record count from the {@OH_UdmfDataLoadInfo}.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfDataLoadInfo](capi-udmf-oh-udmfdataloadinfo.md)* dataLoadInfo | Represents a pointer to an instance of [OH_UdmfDataLoadInfo](capi-udmf-oh-udmfdataloadinfo.md). |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the record count. |

**Reference**:

[OH_UdmfDataLoadInfo](capi-udmf-oh-udmfdataloadinfo.md)


### OH_UdmfDataLoadInfo_SetRecordCount()

```c
void OH_UdmfDataLoadInfo_SetRecordCount(OH_UdmfDataLoadInfo* dataLoadInfo, unsigned int recordCount)
```

**Description**

Sets the record count to the {@OH_UdmfDataLoadInfo}.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UdmfDataLoadInfo](capi-udmf-oh-udmfdataloadinfo.md)* dataLoadInfo | Represents a pointer to an instance of [OH_UdmfDataLoadInfo](capi-udmf-oh-udmfdataloadinfo.md). |
| unsigned int recordCount | Represents the types of data. |

**Reference**:

[OH_UdmfDataLoadInfo](capi-udmf-oh-udmfdataloadinfo.md)



