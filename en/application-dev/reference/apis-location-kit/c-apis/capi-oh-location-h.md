# oh_location.h

## Overview

Define interfaces for querying location switch status, starting locating, and stopping locating.

**Library**: liblocation_ndk.so

**System capability**: SystemCapability.Location.Location.Core

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
| Location_ResultCode | Location functions result code.\n      For a detailed definition, please refer to {@link Location_ResultCode}.\n<br>    {@link LOCAION_SUCCESS} Successfully obtained the location switch status.\n<br>    {@link LOCATION_INVALID_PARAM} The input parameter enabled is a null pointer.\n<br>    {@link LOCATION_SERVICE_UNAVAILABLE} Abnormal startup of location services.\n |

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
| const Location_RequestConfig* requestConfig | - Pointer to the locating request parameters. For details, see {@link Location_RequestConfig}.<br>You can use {@link OH_Location_CreateRequestConfig} to create an instance. |

**Returns**:

| Type | Description |
| -- | -- |
| Location_ResultCode | Location functions result code.\n      For a detailed definition, please refer to {@link Location_ResultCode}.\n<br>    {@link LOCAION_SUCCESS} Successfully start locating.\n<br>    {@link LOCATION_INVALID_PARAM} The input parameter requestConfig is a null pointer.\n<br>    {@link LOCATION_PERMISSION_DENIED} Permission verification failed. The application does not have the\n<br>        permission required to call the API.\n<br>    {@link LOCATION_NOT_SUPPORTED} Capability not supported.\n<br>        Failed to call function due to limited device capabilities.\n<br>    {@link LOCATION_SERVICE_UNAVAILABLE} Abnormal startup of location services.\n<br>    {@link LOCATION_SWITCH_OFF} The location switch is off.\n |

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
| const Location_RequestConfig* requestConfig | - Pointer to the locating request parameters. For details, see {@link Location_RequestConfig}. This parameter needs to be the same as the requestConfig pointer passed in [OH_Location_StartLocating](capi-oh-location-h.md#oh_location_startlocating). |

**Returns**:

| Type | Description |
| -- | -- |
| Location_ResultCode | Location functions result code.\n      For a detailed definition, please refer to {@link Location_ResultCode}.\n<br>    {@link LOCAION_SUCCESS} Successfully stop locationg.\n<br>    {@link LOCATION_INVALID_PARAM} 1.The input parameter is a null pointer.\n<br>        2.Different from the requestConfig pointer passed from [OH_Location_StartLocating](capi-oh-location-h.md#oh_location_startlocating).\n<br>    {@link LOCATION_PERMISSION_DENIED} Permission verification failed. The application does not have the\n<br>        permission required to call the API.\n<br>    {@link LOCATION_NOT_SUPPORTED} Capability not supported.\n<br>        Failed to call function due to limited device capabilities.\n<br>    {@link LOCATION_SERVICE_UNAVAILABLE} Possible reasons: 1. Abnormal startup of location services.\n<br>    {@link LOCATION_SWITCH_OFF} The location switch is off.\n |


