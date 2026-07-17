# HuksKeyStorageType

表示密钥存储方式。

**起始版本：** 8

<!--Device-huks-export enum HuksKeyStorageType--><!--Device-huks-export enum HuksKeyStorageType-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_STORAGE_TEMP

```TypeScript
HUKS_STORAGE_TEMP = 0
```

表示通过本地直接管理密钥。

**说明：** 从API version 8开始支持，从API version 10开始废弃，由于开发者正常使用密钥管理过程中并不需要使用此TAG，故无替代接口。针对密钥派生场景，可使用HUKS_STORAGE_ONLY_USED_IN_HUKS 与 HUKS_STORAGE_KEY_EXPORT_ALLOWED。

**起始版本：** 8

**废弃版本：** 10

<!--Device-HuksKeyStorageType-HUKS_STORAGE_TEMP = 0--><!--Device-HuksKeyStorageType-HUKS_STORAGE_TEMP = 0-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_STORAGE_PERSISTENT

```TypeScript
HUKS_STORAGE_PERSISTENT = 1
```

表示通过HUKS service管理密钥。

**说明：** 从API version 8开始支持，从API version 10开始废弃，由于开发者正常使用密钥管理过程中并不需要使用此TAG，故无替代接口。针对密钥派生场景，可使用HUKS_STORAGE_ONLY_USED_IN_HUKS 与 HUKS_STORAGE_KEY_EXPORT_ALLOWED。

**起始版本：** 8

**废弃版本：** 10

<!--Device-HuksKeyStorageType-HUKS_STORAGE_PERSISTENT = 1--><!--Device-HuksKeyStorageType-HUKS_STORAGE_PERSISTENT = 1-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_STORAGE_ONLY_USED_IN_HUKS

```TypeScript
HUKS_STORAGE_ONLY_USED_IN_HUKS = 2
```

表示主密钥派生的密钥存储于huks中，由HUKS进行托管。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HuksKeyStorageType-HUKS_STORAGE_ONLY_USED_IN_HUKS = 2--><!--Device-HuksKeyStorageType-HUKS_STORAGE_ONLY_USED_IN_HUKS = 2-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本10-11：SystemCapability.Security.Huks.Extension

## HUKS_STORAGE_KEY_EXPORT_ALLOWED

```TypeScript
HUKS_STORAGE_KEY_EXPORT_ALLOWED = 3
```

表示主密钥派生的密钥直接导出给业务方，HUKS不对其进行托管服务。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HuksKeyStorageType-HUKS_STORAGE_KEY_EXPORT_ALLOWED = 3--><!--Device-HuksKeyStorageType-HUKS_STORAGE_KEY_EXPORT_ALLOWED = 3-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本10-11：SystemCapability.Security.Huks.Extension

