# oh_location_type.h

## Overview

Declares the common location attributes.

**Library**: liblocation_ndk.so

**System capability**: SystemCapability.Location.Location.Core

**Since**: 13

**Related module**: [Location](capi-location.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Location_BasicInfo](capi-location-location-basicinfo.md) | Location_BasicInfo | Defines the location information. |
| [Location_Info](capi-location-location-info.md) | Location_Info | Define the structure of location information. |
| [Location_RequestConfig](capi-location-location-requestconfig.md) | Location_RequestConfig | Define the structure of location request parameters. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Location_ResultCode](#location_resultcode) | Location_ResultCode | Enumerates the location result codes. |
| [Location_UseScene](#location_usescene) | Location_UseScene | Enumeration values of use scenarios. |
| [Location_PowerConsumptionScene](#location_powerconsumptionscene) | Location_PowerConsumptionScene | Enumerates the power consumption scenario. |
| [Location_SourceType](#location_sourcetype) | Location_SourceType | Enumerates the source type of location. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [bool OH_LocationInfo_IsFromMock(Location_Info* location)](#oh_locationinfo_isfrommock) | - | Indicates whether the location was obtained from the mock location function. |
| [Location_BasicInfo OH_LocationInfo_GetBasicInfo(Location_Info* location)](#oh_locationinfo_getbasicinfo) | - | Obtain basic location information. |
| [Location_ResultCode OH_LocationInfo_GetAdditionalInfo(Location_Info* location, char* additionalInfo, uint32_t length)](#oh_locationinfo_getadditionalinfo) | - | Obtain additional information from the location information. |
| [typedef void (\*Location_InfoCallback)(Location_Info* location, void* userData)](#location_infocallback) | Location_InfoCallback | Defines the callback function used to report location data. |
| [Location_RequestConfig* OH_Location_CreateRequestConfig(void)](#oh_location_createrequestconfig) | - | Create a location request parameter structure instance. |
| [void OH_Location_DestroyRequestConfig(Location_RequestConfig* requestConfig)](#oh_location_destroyrequestconfig) | - | Destroy the location request parameter instance and reclaim memory. |
| [void OH_LocationRequestConfig_SetUseScene(Location_RequestConfig* requestConfig, Location_UseScene useScene)](#oh_locationrequestconfig_setusescene) | - | Set the use scenario in the location request parameter. Prioritize useScene in the location request parameter [Location_RequestConfig](capi-location-location-requestconfig.md). If useScene is set, powerConsumptionScene becomes invalid. If useScene is not set and powerConsumptionScene is set, this parameter takes effect. If both parameters are not set, the default useScene is [LOCATION_USE_SCENE_DAILY_LIFE_SERVICE](capi-oh-location-type-h.md#location_usescene), and the powerConsumptionCenario parameter is invalid. |
| [void OH_LocationRequestConfig_SetPowerConsumptionScene(Location_RequestConfig* requestConfig, Location_PowerConsumptionScene powerConsumptionScene)](#oh_locationrequestconfig_setpowerconsumptionscene) | - | Set the power consumption scenario in the location request parameters. |
| [void OH_LocationRequestConfig_SetInterval(Location_RequestConfig* requestConfig, int interval)](#oh_locationrequestconfig_setinterval) | - | Set the location reporting interval in the location request parameter. |
| [void OH_LocationRequestConfig_SetCallback(Location_RequestConfig* requestConfig, Location_InfoCallback callback, void* userData)](#oh_locationrequestconfig_setcallback) | - | Set up a callback function for receiving location information. |

### Variable

| Name | Description |
| -- | -- |
| void (*Location_InfoCallback)(Location_Info* location, void* userData) | Defines the callback function used to report location data.<br>**Since**: 13 |

## Enum type description

### Location_ResultCode

```c
enum Location_ResultCode
```

**Description**

Enumerates the location result codes.

**Since**: 13

| Enum item | Description |
| -- | -- |
| LOCATION_SUCCESS = 0 | The operation is successful. |
| LOCATION_PERMISSION_DENIED = 201 | Permission verification failed. The application does not have the permission required to call the API. |
| LOCATION_INVALID_PARAM = 401 | Parameter error. Possible reasons: 1. The input parameter is a null pointer; 2. Parameter values exceed the defined range. |
| LOCATION_NOT_SUPPORTED = 801 | Capability not supported. Failed to call function due to limited device capabilities. |
| LOCATION_SERVICE_UNAVAILABLE = 3301000 | The location service is unavailable. Possible reasons: Abnormal startup of location services. |
| LOCATION_SWITCH_OFF = 3301100 | The location switch is off. |

### Location_UseScene

```c
enum Location_UseScene
```

**Description**

Enumeration values of use scenarios.

**Since**: 13

| Enum item | Description |
| -- | -- |
| LOCATION_USE_SCENE_NAVIGATION = 0x0401 | Indicates the navigation scenario. This feature applies to outdoor scenarios where real-time device locations need to be obtained, such as vehicle-mounted and pedestrian navigation. The GNSS positioning technology is used to provide positioning services, and the power consumption is high. |
| LOCATION_USE_SCENE_SPORT = 0x0402 | Indicates the sport scenario. This feature applies to scenarios where user location tracks are recorded, for example, sports apps. The GNSS positioning technology is used to provide positioning services, and the power consumption is high. |
| LOCATION_USE_SCENE_TRANSPORT = 0x0403 | Indicates a travel scenario. This mode applies to travel scenarios, such as taxi and public transportation. The GNSS positioning technology is used to provide positioning services, and the power consumption is high. |
| LOCATION_USE_SCENE_DAILY_LIFE_SERVICE = 0x0404 | Indicates the daily service usage scenario. This mode applies to scenarios where precise user location is not required, such as news, online shopping, and ordering applications. In this scenario, only a network positioning technology is used to provide a positioning service, and power consumption is relatively low. |

### Location_PowerConsumptionScene

```c
enum Location_PowerConsumptionScene
```

**Description**

Enumerates the power consumption scenario.

**Since**: 13

| Enum item | Description |
| -- | -- |
| LOCATION_HIGH_POWER_CONSUMPTION = 0x0601 | High power consumption. GNSS positioning technology is mainly used. We will use network positioning technology to provide services before GNSS provides stable location results; During continuous positioning, if the GNSS positioning result cannot be obtained for more than 30 seconds, the network positioning technology is used to obtain the location. Consumes a large number of hardware resources and power. |
| LOCATION_LOW_POWER_CONSUMPTION = 0x0602 | Low power consumption. This mode applies to scenarios that do not require high user location precision, such as news, online shopping, and meal ordering. In this scenario, only a network positioning technology is used to provide a positioning service, and power consumption is relatively low. |
| LOCATION_NO_POWER_CONSUMPTION = 0x0603 | No power consumption. In this scenario, the location is not proactively triggered. The location is returned to the current app only when other apps are located. |

### Location_SourceType

```c
enum Location_SourceType
```

**Description**

Enumerates the source type of location.

**Since**: 13

| Enum item | Description |
| -- | -- |
| LOCATION_SOURCE_TYPE_GNSS = 1 | The positioning result is based on the GNSS positioning technology. |
| LOCATION_SOURCE_TYPE_NETWORK = 2 | The positioning result comes from the network positioning technology. |
| LOCATION_SOURCE_TYPE_INDOOR = 3 | The positioning result comes from the high-precision indoor positioning technology. |
| LOCATION_SOURCE_TYPE_RTK = 4 | The positioning result comes from the high-precision positioning technology. |


## Function description

### OH_LocationInfo_IsFromMock()

```c
bool OH_LocationInfo_IsFromMock(Location_Info* location)
```

**Description**

Indicates whether the location was obtained from the mock location function.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Location_Info](capi-location-location-info.md)* location | - Pointer to the location information structure. A non‑null pointer is required. The pointer can be obtained via [Location_InfoCallback](capi-oh-location-type-h.md#location_infocallback). |

**Returns**:

| Type | Description |
| -- | -- |
| bool | true if the location was obtained from the mock location function.  Otherwise, the location originates from the system's real positioning result. |

### OH_LocationInfo_GetBasicInfo()

```c
Location_BasicInfo OH_LocationInfo_GetBasicInfo(Location_Info* location)
```

**Description**

Obtain basic location information.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Location_Info](capi-location-location-info.md)* location | - Pointer to the location information structure. A non-null pointer is required. The pointer can be obtained from [Location_InfoCallback](capi-oh-location-type-h.md#location_infocallback). |

**Returns**:

| Type | Description |
| -- | -- |
| [Location_BasicInfo](capi-location-location-basicinfo.md) | Return the basic information structure of the location.\n  For a detailed definition, please refer to [Location_BasicInfo](capi-location-location-basicinfo.md).\n |

### OH_LocationInfo_GetAdditionalInfo()

```c
Location_ResultCode OH_LocationInfo_GetAdditionalInfo(Location_Info* location, char* additionalInfo, uint32_t length)
```

**Description**

Obtain additional information from the location information.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Location_Info](capi-location-location-info.md)* location | - Pointer to the location information structure. A non-null pointer is required. The pointer can be obtained from [Location_InfoCallback](capi-oh-location-type-h.md#location_infocallback). |
| char* additionalInfo | - Non null pointers of char type; This variable is used to store additional information strings. The string is in JSON format. The pointer and the corresponding memory are created by the caller. You are advised to apply for a memory of 256 bytes or more. If a null pointer is passed, an error code is returned. |
| uint32_t length | - Memory size of additionalInfo. |

**Returns**:

| Type | Description |
| -- | -- |
| [Location_ResultCode](capi-oh-location-type-h.md#location_resultcode) | Location functions result code.\n      For a detailed definition, please refer to [Location_ResultCode](capi-oh-location-type-h.md#location_resultcode).\n<br>    {@link LOCAION_SUCCESS} Successfully obtained additional information.\n<br>    [LOCATION_INVALID_PARAM](capi-oh-location-type-h.md#location_resultcode) 1.The input parameter location or additionalInfo is a null pointer.\n          2.The input parameter length is too small to store additional information.\n |

### Location_InfoCallback()

```c
typedef void (*Location_InfoCallback)(Location_Info* location, void* userData)
```

**Description**

Defines the callback function used to report location data.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Location_Info](capi-location-location-info.md)\* location | - Pointer to the [Location_Info](capi-location-location-info.md) instance. Carry the latest location information. The memory of the location instance is recycled at the end of [Location_InfoCallback](capi-oh-location-type-h.md#location_infocallback). Before that, call [OH_LocationInfo_GetBasicInfo](capi-oh-location-type-h.md#oh_locationinfo_getbasicinfo) and other interfaces to obtain location information. |
| void\* userData | - Pointer to an application data structure, this parameter is passed in through [OH_LocationRequestConfig_SetCallback](capi-oh-location-type-h.md#oh_locationrequestconfig_setcallback). |

### OH_Location_CreateRequestConfig()

```c
Location_RequestConfig* OH_Location_CreateRequestConfig(void)
```

**Description**

Create a location request parameter structure instance.

**Since**: 13

**Returns**:

| Type | Description |
| -- | -- |
| [Location_RequestConfig*](capi-location-location-requestconfig.md) | Return a pointer to the {@ link Location_RequestConfig} instance. \n  If NULL is returned, it indicates that the creation failed. \n  The possible reason is that the application address space is full,\n  resulting in the inability to allocate space. \n |

### OH_Location_DestroyRequestConfig()

```c
void OH_Location_DestroyRequestConfig(Location_RequestConfig* requestConfig)
```

**Description**

Destroy the location request parameter instance and reclaim memory.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Location_RequestConfig](capi-location-location-requestconfig.md)* requestConfig | - Pointer to [Location_RequestConfig](capi-location-location-requestconfig.md) instance. The instance was created by [OH_Location_CreateRequestConfig](capi-oh-location-type-h.md#oh_location_createrequestconfig). |

### OH_LocationRequestConfig_SetUseScene()

```c
void OH_LocationRequestConfig_SetUseScene(Location_RequestConfig* requestConfig, Location_UseScene useScene)
```

**Description**

Set the use scenario in the location request parameter. Prioritize useScene in the location request parameter [Location_RequestConfig](capi-location-location-requestconfig.md). If useScene is set, powerConsumptionScene becomes invalid. If useScene is not set and powerConsumptionScene is set, this parameter takes effect. If both parameters are not set, the default useScene is [LOCATION_USE_SCENE_DAILY_LIFE_SERVICE](capi-oh-location-type-h.md#location_usescene), and the powerConsumptionCenario parameter is invalid.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Location_RequestConfig](capi-location-location-requestconfig.md)* requestConfig | - Pointer to the [Location_RequestConfig](capi-location-location-requestconfig.md) instance. The instance was created by [OH_Location_CreateRequestConfig](capi-oh-location-type-h.md#oh_location_createrequestconfig). |
| [Location_UseScene](capi-oh-location-type-h.md#location_usescene) useScene | - Representing the use scenario during location requests. The default value is [LOCATION_USE_SCENE_DAILY_LIFE_SERVICE](capi-oh-location-type-h.md#location_usescene). For a detailed definition, please refer to [Location_UseScene](capi-oh-location-type-h.md#location_usescene). |

### OH_LocationRequestConfig_SetPowerConsumptionScene()

```c
void OH_LocationRequestConfig_SetPowerConsumptionScene(Location_RequestConfig* requestConfig, Location_PowerConsumptionScene powerConsumptionScene)
```

**Description**

Set the power consumption scenario in the location request parameters.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Location_RequestConfig](capi-location-location-requestconfig.md)* requestConfig | - Pointer to the [Location_RequestConfig](capi-location-location-requestconfig.md) instance. The instance was created by [OH_Location_CreateRequestConfig](capi-oh-location-type-h.md#oh_location_createrequestconfig). |
| [Location_PowerConsumptionScene](capi-oh-location-type-h.md#location_powerconsumptionscene) powerConsumptionScene | - Represents the power consumption scenario for location requests. The recognition value is [LOCATION_LOW_POWER_CONSUMPTION](capi-oh-location-type-h.md#location_powerconsumptionscene). For a detailed definition, please refer to [Location_PowerConsumptionScene](capi-oh-location-type-h.md#location_powerconsumptionscene). |

### OH_LocationRequestConfig_SetInterval()

```c
void OH_LocationRequestConfig_SetInterval(Location_RequestConfig* requestConfig, int interval)
```

**Description**

Set the location reporting interval in the location request parameter.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Location_RequestConfig](capi-location-location-requestconfig.md)* requestConfig | - Pointer to the [Location_RequestConfig](capi-location-location-requestconfig.md) instance. The instance was created by [OH_Location_CreateRequestConfig](capi-oh-location-type-h.md#oh_location_createrequestconfig). |
| int interval | - Indicates the time interval for location reporting, in seconds. The value is greater than or equal to 1. The default value is 1. |

### OH_LocationRequestConfig_SetCallback()

```c
void OH_LocationRequestConfig_SetCallback(Location_RequestConfig* requestConfig, Location_InfoCallback callback, void* userData)
```

**Description**

Set up a callback function for receiving location information.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Location_RequestConfig](capi-location-location-requestconfig.md)* requestConfig | - Pointer to the [Location_RequestConfig](capi-location-location-requestconfig.md) instance. The instance was created by [OH_Location_CreateRequestConfig](capi-oh-location-type-h.md#oh_location_createrequestconfig). |
| [Location_InfoCallback](capi-oh-location-type-h.md#location_infocallback) callback | - Pointer to the callback function for receiving the location. For details, see [Location_InfoCallback](capi-oh-location-type-h.md#location_infocallback). |
| void* userData | - Pointer to the application data structure, which will be carried in the callback function. |


