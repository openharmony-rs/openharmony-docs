# deviceinfo.h

## Overview

Declares the APIs for querying device information.

**Library**: libdeviceinfo_ndk.z.so

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Related module**: [DeviceInfo](capi-deviceinfo.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [const char *OH_GetDeviceType(void)](#oh_getdevicetype) | Obtains the device type. |
| [const char *OH_GetManufacture(void)](#oh_getmanufacture) | Obtains the device manufacturer. |
| [const char *OH_GetBrand(void)](#oh_getbrand) | Obtains the device brand. |
| [const char *OH_GetMarketName(void)](#oh_getmarketname) | Obtains the market name. |
| [const char *OH_GetProductSeries(void)](#oh_getproductseries) | Obtains the product series. |
| [const char *OH_GetProductModel(void)](#oh_getproductmodel) | Obtains the product model. |
| [const char *OH_GetSoftwareModel(void)](#oh_getsoftwaremodel) | Obtains the software model. |
| [const char *OH_GetHardwareModel(void)](#oh_gethardwaremodel) | Obtains the hardware model. |
| [const char *OH_GetBootloaderVersion(void)](#oh_getbootloaderversion) | Obtains the Bootloader version. |
| [const char *OH_GetAbiList(void)](#oh_getabilist) | Obtains the ABI list. |
| [const char *OH_GetSecurityPatchTag(void)](#oh_getsecuritypatchtag) | Obtains the security patch tag. |
| [const char *OH_GetDisplayVersion(void)](#oh_getdisplayversion) | Obtains the display version. |
| [const char *OH_GetIncrementalVersion(void)](#oh_getincrementalversion) | Obtains the incremental version. |
| [const char *OH_GetOsReleaseType(void)](#oh_getosreleasetype) | Obtains the OS release type represented by a string. |
| [const char *OH_GetOSFullName(void)](#oh_getosfullname) | Obtains the OS full name. |
| [int OH_GetSdkApiVersion(void)](#oh_getsdkapiversion) | Obtains the SDK API version. |
| [int OH_GetFirstApiVersion(void)](#oh_getfirstapiversion) | Obtains the first API version. |
| [const char *OH_GetVersionId(void)](#oh_getversionid) | Obtains the version ID. |
| [const char *OH_GetBuildType(void)](#oh_getbuildtype) | Obtains the build type. |
| [const char *OH_GetBuildUser(void)](#oh_getbuilduser) | Obtains the build user. |
| [const char *OH_GetBuildHost(void)](#oh_getbuildhost) | Obtains the build host. |
| [const char *OH_GetBuildTime(void)](#oh_getbuildtime) | Obtains the build time. |
| [const char *OH_GetBuildRootHash(void)](#oh_getbuildroothash) | Obtains the build root hash. |
| [const char *OH_GetDistributionOSName(void)](#oh_getdistributionosname) | Obtains the Distribution OS name represented by a string. |
| [const char *OH_GetDistributionOSVersion(void)](#oh_getdistributionosversion) | Obtains the ISV distribution OS version. |
| [int OH_GetDistributionOSApiVersion(void)](#oh_getdistributionosapiversion) | Obtains the ISV distribution OS API version. |
| [const char *OH_GetDistributionOSReleaseType(void)](#oh_getdistributionosreleasetype) | Obtains the ISV distribution OS release type. |

## Function description

### OH_GetDeviceType()

```c
const char *OH_GetDeviceType(void)
```

**Description**

Obtains the device type.

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns one of the following values:      <br>phone (or default),      <br>wearable,      <br>liteWearable,      <br>tablet,      <br>tv,      <br>car,      <br>smartVision |

### OH_GetManufacture()

```c
const char *OH_GetManufacture(void)
```

**Description**

Obtains the device manufacturer.

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns a device manufacturer. The value is of the string type. |

### OH_GetBrand()

```c
const char *OH_GetBrand(void)
```

**Description**

Obtains the device brand.

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns a device brand. The value is of the string type. |

### OH_GetMarketName()

```c
const char *OH_GetMarketName(void)
```

**Description**

Obtains the market name.

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns a market name. The value is of the string type. |

### OH_GetProductSeries()

```c
const char *OH_GetProductSeries(void)
```

**Description**

Obtains the product series.

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns the product series. The value is of the string type. |

### OH_GetProductModel()

```c
const char *OH_GetProductModel(void)
```

**Description**

Obtains the product model.

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns a product model. The value is of the string type. |

### OH_GetSoftwareModel()

```c
const char *OH_GetSoftwareModel(void)
```

**Description**

Obtains the software model.

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns a software model. The value is of the string type. |

### OH_GetHardwareModel()

```c
const char *OH_GetHardwareModel(void)
```

**Description**

Obtains the hardware model.

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns a hardware model. The value is of the string type. |

### OH_GetBootloaderVersion()

```c
const char *OH_GetBootloaderVersion(void)
```

**Description**

Obtains the Bootloader version.

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns a Bootloader version. The value is of the string type. |

### OH_GetAbiList()

```c
const char *OH_GetAbiList(void)
```

**Description**

Obtains the ABI list.

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns an ABI list. The value is of the string type. |

### OH_GetSecurityPatchTag()

```c
const char *OH_GetSecurityPatchTag(void)
```

**Description**

Obtains the security patch tag.

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns a security patch tag. The value is of the string type. |

### OH_GetDisplayVersion()

```c
const char *OH_GetDisplayVersion(void)
```

**Description**

Obtains the display version.

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns a display version. The value is of the string type. |

### OH_GetIncrementalVersion()

```c
const char *OH_GetIncrementalVersion(void)
```

**Description**

Obtains the incremental version.

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns an incremental version. The value is of the string type. |

### OH_GetOsReleaseType()

```c
const char *OH_GetOsReleaseType(void)
```

**Description**

Obtains the OS release type represented by a string.

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns an OS release type. The options include Release, Beta, and Canary.      <br>A specific release type may be Release, Beta1, or another similar type. |

### OH_GetOSFullName()

```c
const char *OH_GetOSFullName(void)
```

**Description**

Obtains the OS full name.

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns an OS full name. The value is of the string type. |

### OH_GetSdkApiVersion()

```c
int OH_GetSdkApiVersion(void)
```

**Description**

Obtains the SDK API version.

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns an SDK API version. |

### OH_GetFirstApiVersion()

```c
int OH_GetFirstApiVersion(void)
```

**Description**

Obtains the first API version.

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the first API version. |

### OH_GetVersionId()

```c
const char *OH_GetVersionId(void)
```

**Description**

Obtains the version ID.

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns a version ID. The value is of the string type. |

### OH_GetBuildType()

```c
const char *OH_GetBuildType(void)
```

**Description**

Obtains the build type.

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns a build type. The value is of the string type. |

### OH_GetBuildUser()

```c
const char *OH_GetBuildUser(void)
```

**Description**

Obtains the build user.

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns a build user. The value is of the string type. |

### OH_GetBuildHost()

```c
const char *OH_GetBuildHost(void)
```

**Description**

Obtains the build host.

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns a build host. The value is of the string type. |

### OH_GetBuildTime()

```c
const char *OH_GetBuildTime(void)
```

**Description**

Obtains the build time.

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns the build time. The value is of the string type. |

### OH_GetBuildRootHash()

```c
const char *OH_GetBuildRootHash(void)
```

**Description**

Obtains the build root hash.

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns a build root hash. The value is of the string type. |

### OH_GetDistributionOSName()

```c
const char *OH_GetDistributionOSName(void)
```

**Description**

Obtains the Distribution OS name represented by a string.

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns an ISV distribution OS name.      <br>If no ISV is specified, an empty string is returned. |

### OH_GetDistributionOSVersion()

```c
const char *OH_GetDistributionOSVersion(void)
```

**Description**

Obtains the ISV distribution OS version.

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns an ISV distribution OS version.      <br>If no ISV is specified, the value of [OH_GetOSFullName](capi-deviceinfo-h.md#oh_getosfullname) is returned. |

### OH_GetDistributionOSApiVersion()

```c
int OH_GetDistributionOSApiVersion(void)
```

**Description**

Obtains the ISV distribution OS API version.

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns an ISV distribution OS API version.      <br>If no ISV is specified, the value of [OH_GetSdkApiVersion](capi-deviceinfo-h.md#oh_getsdkapiversion) is returned. |

### OH_GetDistributionOSReleaseType()

```c
const char *OH_GetDistributionOSReleaseType(void)
```

**Description**

Obtains the ISV distribution OS release type.

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns an ISV distribution OS release type.      <br>If no ISV is specified, the value of [OH_GetOsReleaseType](capi-deviceinfo-h.md#oh_getosreleasetype) is returned. |


