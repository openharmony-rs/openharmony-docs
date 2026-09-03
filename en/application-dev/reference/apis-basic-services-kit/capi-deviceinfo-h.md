# deviceinfo.h
<!--Kit: Basic Services Kit-->
<!--Subsystem: Startup-->
<!--Owner: @chenjinxiang3-->
<!--Designer: @chenjinxiang3-->
<!--Tester: @liuhaonan2-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=7630e5b891554540841eebb43cca63e5770c749e translatedAt=2026-09-01T03:02:06.873Z pushedAt=2026-09-01T06:32:52.869Z -->

## Overview

Declares the APIs for querying device information. This module provides the capability of obtaining basic device information, such as the device type, manufacturer, brand, model, and version. It can be used to adapt device features, collect device information, or manage devices. These APIs obtain device information by reading system properties. The return value is a pointer to a constant string. The pointer points to the data stored in the system. The caller does not need to release the memory.

**File to include**: <deviceinfo.h>

**Library**: libdeviceinfo_ndk.z.so

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Related modules**: [DeviceInfo](capi-deviceinfo.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [const char *OH_GetDeviceType(void)](#oh_getdevicetype) | Obtains the device type.|
| [const char *OH_GetManufacture(void)](#oh_getmanufacture) | Obtains the device manufacturer.|
| [const char *OH_GetBrand(void)](#oh_getbrand) | Obtains the device brand.|
| [const char *OH_GetMarketName(void)](#oh_getmarketname) | Obtains the external product series, that is, the market name. |
| [const char *OH_GetProductSeries(void)](#oh_getproductseries) | Obtains the product series.|
| [const char *OH_GetProductModel(void)](#oh_getproductmodel) | Obtains the product model.|
| [const char *OH_GetSoftwareModel(void)](#oh_getsoftwaremodel) | Obtains the software model.|
| [const char *OH_GetHardwareModel(void)](#oh_gethardwaremodel) | Obtains the hardware model.|
| [const char *OH_GetBootloaderVersion(void)](#oh_getbootloaderversion) | Obtains the Bootloader version.|
| [const char *OH_GetAbiList(void)](#oh_getabilist) | Obtains the application binary interface (ABI) list.|
| [const char *OH_GetSecurityPatchTag(void)](#oh_getsecuritypatchtag) | Obtains the security patch tag.|
| [const char *OH_GetDisplayVersion(void)](#oh_getdisplayversion) | Obtains the display version.|
| [const char *OH_GetIncrementalVersion(void)](#oh_getincrementalversion) | Obtains the incremental version.|
| [const char *OH_GetOsReleaseType(void)](#oh_getosreleasetype) | Obtains the OS release type.|
| [const char *OH_GetOSFullName(void)](#oh_getosfullname) | Obtains the OS full name.|
| [int OH_GetSdkApiVersion(void)](#oh_getsdkapiversion) | Obtains the SDK API version.|
| [int OH_GetFirstApiVersion(void)](#oh_getfirstapiversion) | Obtains the first API version.|
| [const char *OH_GetVersionId(void)](#oh_getversionid) | Obtains the version ID.|
| [const char *OH_GetBuildType(void)](#oh_getbuildtype) | Obtains the build type.|
| [const char *OH_GetBuildUser(void)](#oh_getbuilduser) | Obtains the build user.|
| [const char *OH_GetBuildHost(void)](#oh_getbuildhost) | Obtains the build host.|
| [const char *OH_GetBuildTime(void)](#oh_getbuildtime) | Obtains the build time.|
| [const char *OH_GetBuildRootHash(void)](#oh_getbuildroothash) | Obtains the build root hash.|
| [const char *OH_GetDistributionOSName(void)](#oh_getdistributionosname) | Obtains the ISV distribution OS name. ISVs can use their own OS names. |
| [const char *OH_GetDistributionOSVersion(void)](#oh_getdistributionosversion) | Obtains the ISV distribution OS version.|
| [int OH_GetDistributionOSApiVersion(void)](#oh_getdistributionosapiversion) | Obtains the ISV distribution OS version. |
| [const char *OH_GetDistributionOSReleaseType(void)](#oh_getdistributionosreleasetype) | Obtains the ISV distribution OS release type.|

## Function Description

### OH_GetDeviceType()

```c
const char *OH_GetDeviceType(void)
```

**Description**

Obtains the device type. This API returns a predefined device type in the form of a string.

**Since**: 10

**Returns**

| Type| Description|
| -- | -- |
| const char* | Device type as a string. The options are as follows:<br>• **phone**<br>• **default**: default value returned when the device type cannot be identified<br>• **wearable**<br>• **liteWearable**<br>• **tablet**<br>• **tv**<br>• **car**<br>• **smartVision** |

### OH_GetManufacture()

```c
const char *OH_GetManufacture(void)
```

**Description**

Obtains the device manufacturer.

**Since**: 10

**Returns**

| Type| Description|
| -- | -- |
| const char* | Returns a device manufacturer. The value is of the string type.|

### OH_GetBrand()

```c
const char *OH_GetBrand(void)
```

**Description**

Obtains the device brand.

**Since**: 10

**Returns**

| Type| Description|
| -- | -- |
| const char* | Returns a device brand. The value is of the string type.|

### OH_GetMarketName()

```c
const char *OH_GetMarketName(void)
```

**Description**

Obtains the external product series, that is, the market name.

**Since**: 10

**Returns**

| Type| Description|
| -- | -- |
| const char* | Returns a market name. The value is of the string type.|

### OH_GetProductSeries()

```c
const char *OH_GetProductSeries(void)
```

**Description**

Obtains the product series.

**Since**: 10

**Returns**

| Type| Description|
| -- | -- |
| const char* | Returns the product series. The value is of the string type.|

### OH_GetProductModel()

```c
const char *OH_GetProductModel(void)
```

**Description**

Obtains the product model.

**Since**: 10

**Returns**

| Type| Description|
| -- | -- |
| const char* | Returns a product model. The value is of the string type.|

### OH_GetSoftwareModel()

```c
const char *OH_GetSoftwareModel(void)
```

**Description**

Obtains the software model. When the same software version is used on different hardware models, this field is used to distinguish different software branches.

**Since**: 10

**Returns**

| Type| Description|
| -- | -- |
| const char* | Returns a software model. The value is of the string type.|

### OH_GetHardwareModel()

```c
const char *OH_GetHardwareModel(void)
```

**Description**

Obtains the hardware model.

**Since**: 10

**Returns**

| Type| Description|
| -- | -- |
| const char* | Hardware model. The value is of the string type. Common values include **TASA00CVN1**. |

### OH_GetBootloaderVersion()

```c
const char *OH_GetBootloaderVersion(void)
```

**Description**

Obtains the Bootloader version.

**Since**: 10

**Returns**

| Type| Description|
| -- | -- |
| const char* | Bootloader version. The value is of the string type. Common values include **bootloader**. |

### OH_GetAbiList()

```c
const char *OH_GetAbiList(void)
```

**Description**

Obtains the ABI list.

**Since**: 10

**Returns**

| Type| Description|
| -- | -- |
| const char* | ABI list supported. The value is of the string type. Multiple values are separated by commas (,). Common values include **arm64-v8a**. |

### OH_GetSecurityPatchTag()

```c
const char *OH_GetSecurityPatchTag(void)
```

**Description**

Obtains the security patch tag.

**Since**: 10

**Returns**

| Type| Description|
| -- | -- |
| const char* | Security patch tag. The value is of the string type. The format is **YYYY/MM/DD**, for example, **2023/10/05**, indicating the release date of the security patch. |

### OH_GetDisplayVersion()

```c
const char *OH_GetDisplayVersion(void)
```

**Description**

Obtains the display version.

**Since**: 10

**Returns**

| Type| Description|
| -- | -- |
| const char* | Product version of the device. The value is of the string type. |

### OH_GetIncrementalVersion()

```c
const char *OH_GetIncrementalVersion(void)
```

**Description**

Obtains the incremental version.

**Since**: 10

**Returns**

| Type| Description|
| -- | -- |
| const char* | Incremental version. The value is of the string type. Common values include **6.1.1.120**. |

### OH_GetOsReleaseType()

```c
const char *OH_GetOsReleaseType(void)
```

**Description**

Obtains the OS release type. This API returns a predefined OS release type in the form of a string.

**Since**: 10

**Returns**

| Type| Description                                                                                     |
| -- |-----------------------------------------------------------------------------------------|
| const char* | OS release type. The options include **Release**, **Beta**, and **Canary**<br> A specific release type can be **release** or **Beta1**.<br>-&nbsp;**Canary**: Preliminary release open only to specific developers. This release does not promise API stability and may require tolerance of instability.<br>-&nbsp;**Beta**: Release open to all developers. This release does not promise API stability and may require tolerance of instability.<br>-&nbsp;**Release**: Official release open to all developers. This release promises that all APIs are stable. |

### OH_GetOSFullName()

```c
const char *OH_GetOSFullName(void)
```

**Description**

Obtains the OS full name.

**Since**: 10

**Returns**

| Type| Description|
| -- | -- |
| const char* | Full OS name. The value is of the string type. The version format is **OpenHarmony-x.x.x.x**. |

### OH_GetSdkApiVersion()

```c
int OH_GetSdkApiVersion(void)
```

**Description**

Obtains the SDK API version.

**Since**: 10

**Returns**

| Type| Description|
| -- | -- |
| int | SDK API version. The value is an integer. Common values include **12**. |

### OH_GetFirstApiVersion()

```c
int OH_GetFirstApiVersion(void)
```

**Description**

Obtains the first API version, which is the API version supported by the device when it was first released.

**Since**: 10

**Returns**

| Type| Description|
| -- | -- |
| int | First API version, which is the API version supported by the device when it was first released. The value is an integer. Common values include **3**. |

### OH_GetVersionId()

```c
const char *OH_GetVersionId(void)
```

**Description**

Obtains the version ID.

**Since**: 10

**Returns**

| Type| Description|
| -- | -- |
| const char* | Returns a version ID. The value is of the string type.|

### OH_GetBuildType()

```c
const char *OH_GetBuildType(void)
```

**Description**

Obtains the build type.

**Since**: 10

**Returns**

| Type| Description|
| -- | -- |
| const char* | Build type. The value is of the string type. The default value is **default**. |

### OH_GetBuildUser()

```c
const char *OH_GetBuildUser(void)
```

**Description**

Obtains the build user.

**Since**: 10

**Returns**

| Type| Description|
| -- | -- |
| const char* | Build type. The value is of the string type. The default value is **default**. |

### OH_GetBuildHost()

```c
const char *OH_GetBuildHost(void)
```

**Description**

Obtains the build host.

**Since**: 10

**Returns**

| Type| Description|
| -- | -- |
| const char* | Build host. The value is of the string type. The default value is **default**. |

### OH_GetBuildTime()

```c
const char *OH_GetBuildTime(void)
```

**Description**

Obtains the build time.

**Since**: 10

**Returns**

| Type| Description|
| -- | -- |
| const char* | Build time, indicating the timestamp when the OS version is built. The value is of the string type. Common values include **1783430505910**. |

### OH_GetBuildRootHash()

```c
const char *OH_GetBuildRootHash(void)
```

**Description**

Obtains the build root hash.

**Since**: 10

**Returns**

| Type| Description|
| -- | -- |
| const char* | Build root hash. The value is of the string type. The default value is **default**. |

### OH_GetDistributionOSName()

```c
const char *OH_GetDistributionOSName(void)
```

**Description**

Obtains the ISV distribution OS name. ISVs can use their own OS names.

**Since**: 10

**Returns**

| Type| Description|
| -- | -- |
| const char* | ISV distribution OS name. If no ISV is specified, an empty string is returned. |

### OH_GetDistributionOSVersion()

```c
const char *OH_GetDistributionOSVersion(void)
```

**Description**

Obtains the ISV distribution OS version.

**Since**: 10

**Returns**

| Type| Description                                                                        |
| -- |----------------------------------------------------------------------------|
| const char* | Returns an ISV distribution OS version.<br> If no ISV is specified, the value of [OH_GetOSFullName](#oh_getosfullname) is returned.|

### OH_GetDistributionOSApiVersion()

```c
int OH_GetDistributionOSApiVersion(void)
```

**Description**

Obtains the ISV distribution OS API version.

**Since**: 10

**Returns**

| Type| Description|
| -- | -- |
| int | ISV distribution OS API version. If no ISV is specified, the value of [OH_GetSdkApiVersion](#oh_getsdkapiversion) is returned. |

### OH_GetDistributionOSReleaseType()

```c
const char *OH_GetDistributionOSReleaseType(void)
```

**Description**

Obtains the ISV distribution OS release type.

**Since**: 10

**Returns**

| Type| Description                                                                             |
| -- |---------------------------------------------------------------------------------|
| const char* | ISV distribution OS release type. If no ISV is specified, the value of [OH_GetOsReleaseType](#oh_getosreleasetype) is returned. |

