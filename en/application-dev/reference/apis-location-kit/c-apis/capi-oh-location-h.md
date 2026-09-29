# oh_location.h

## Overview

Define interfaces for querying location switch status, starting locating, and stopping locating.

**Library**: liblocation_ndk.so

**Since**: 13

**Related module**: [Location](capi-location.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [Location_ResultCode OH_Location_IsLocatingEnabled(bool* enabled)](#oh_location_islocatingenabled) | Check whether the location switch is enabled. |
| [Location_ResultCode OH_Location_StartLocating(const Location_RequestConfig* requestConfig)](#oh_location_startlocating) | Start locating and subscribe location changed. |
| [Location_ResultCode OH_Location_StopLocating(const Location_RequestConfig* requestConfig)](#oh_location_stoplocating) | Stop locating and unsubscribe location changed. |

## Function description

### OH_Location_IsLocatingEnabled()

```c
Location_ResultCode OH_Location_IsLocatingEnabled(bool* enabled)
```

**Description**

Check whether the location switch is enabled.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| bool* enabled | - It is a boolean pointer used to receive location switch status values. Equal to true indicates that the location switch is turned on, false indicates that the location switch is turned off. The caller needs to pass in a non empty boolean pointer, otherwise an error will be returned. |

**Returns**:

| Type | Description |
| -- | -- |
| [Location_ResultCode](capi-oh-location-type-h.md#location_resultcode) | Location functions result code.\n For a detailed definition, please refer to [Location_ResultCode](capi-oh-location-type-h.md#location_resultcode).\n LOCAION_SUCCESS Successfully obtained the location switch status.\n [LOCATION_INVALID_PARAM](capi-oh-location-type-h.md#location_resultcode) The input parameter enabled is a null pointer.\n [LOCATION_SERVICE_UNAVAILABLE](capi-oh-location-type-h.md#location_resultcode) Abnormal startup of location services.\n |

### OH_Location_StartLocating()

```c
Location_ResultCode OH_Location_StartLocating(const Location_RequestConfig* requestConfig)
```

**Description**

Start locating and subscribe location changed.

**Required permission**: ohos.permission.APPROXIMATELY_LOCATION

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Location_RequestConfig](capi-location-location-requestconfig.md)* requestConfig | - Pointer to the locating request parameters. For details, see [Location_RequestConfig](capi-location-location-requestconfig.md). You can use [OH_Location_CreateRequestConfig](capi-oh-location-type-h.md#oh_location_createrequestconfig) to create an instance. |

**Returns**:

| Type | Description |
| -- | -- |
| [Location_ResultCode](capi-oh-location-type-h.md#location_resultcode) | Location functions result code.\n For a detailed definition, please refer to [Location_ResultCode](capi-oh-location-type-h.md#location_resultcode).\n LOCAION_SUCCESS Successfully start locating.\n [LOCATION_INVALID_PARAM](capi-oh-location-type-h.md#location_resultcode) The input parameter requestConfig is a null pointer.\n [LOCATION_PERMISSION_DENIED](capi-oh-location-type-h.md#location_resultcode) Permission verification failed. The application does not have the\n permission required to call the API.\n [LOCATION_NOT_SUPPORTED](capi-oh-location-type-h.md#location_resultcode) Capability not supported.\n Failed to call function due to limited device capabilities.\n [LOCATION_SERVICE_UNAVAILABLE](capi-oh-location-type-h.md#location_resultcode) Abnormal startup of location services.\n [LOCATION_SWITCH_OFF](capi-oh-location-type-h.md#location_resultcode) The location switch is off.\n |

### OH_Location_StopLocating()

```c
Location_ResultCode OH_Location_StopLocating(const Location_RequestConfig* requestConfig)
```

**Description**

Stop locating and unsubscribe location changed.

**Required permission**: ohos.permission.APPROXIMATELY_LOCATION

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Location_RequestConfig](capi-location-location-requestconfig.md)* requestConfig | - Pointer to the locating request parameters. For details, see [Location_RequestConfig](capi-location-location-requestconfig.md). This parameter needs to be the same as the requestConfig pointer passed in [OH_Location_StartLocating](capi-oh-location-h.md#oh_location_startlocating). |

**Returns**:

| Type | Description |
| -- | -- |
| [Location_ResultCode](capi-oh-location-type-h.md#location_resultcode) | Location functions result code.\n For a detailed definition, please refer to [Location_ResultCode](capi-oh-location-type-h.md#location_resultcode).\n LOCAION_SUCCESS Successfully stop locationg.\n [LOCATION_INVALID_PARAM](capi-oh-location-type-h.md#location_resultcode) 1.The input parameter is a null pointer.\n 2.Different from the requestConfig pointer passed from [OH_Location_StartLocating](capi-oh-location-h.md#oh_location_startlocating).\n [LOCATION_PERMISSION_DENIED](capi-oh-location-type-h.md#location_resultcode) Permission verification failed. The application does not have the\n permission required to call the API.\n [LOCATION_NOT_SUPPORTED](capi-oh-location-type-h.md#location_resultcode) Capability not supported.\n Failed to call function due to limited device capabilities.\n [LOCATION_SERVICE_UNAVAILABLE](capi-oh-location-type-h.md#location_resultcode) Possible reasons: 1. Abnormal startup of location services.\n [LOCATION_SWITCH_OFF](capi-oh-location-type-h.md#location_resultcode) The location switch is off.\n |


