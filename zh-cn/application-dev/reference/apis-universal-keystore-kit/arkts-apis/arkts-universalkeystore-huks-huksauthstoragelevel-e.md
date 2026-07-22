# HuksAuthStorageLevel

表示生成或导入密钥时，指定该密钥的存储安全等级。
> **说明：**  
>  
> 业务在使用存储等级为ECE的密钥时，建议通过感知  
> [锁屏事件](../../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_screen_locked)  
> 来清理使用该密钥创建的会话资源，以保证安全性。

**起始版本：** 11

<!--Device-huks-export enum HuksAuthStorageLevel--><!--Device-huks-export enum HuksAuthStorageLevel-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本11：SystemCapability.Security.Huks.Extension

## HUKS_AUTH_STORAGE_LEVEL_DE

```TypeScript
HUKS_AUTH_STORAGE_LEVEL_DE = 0
```

表示密钥仅在开机后可访问。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HuksAuthStorageLevel-HUKS_AUTH_STORAGE_LEVEL_DE = 0--><!--Device-HuksAuthStorageLevel-HUKS_AUTH_STORAGE_LEVEL_DE = 0-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本11：SystemCapability.Security.Huks.Extension

## HUKS_AUTH_STORAGE_LEVEL_CE

```TypeScript
HUKS_AUTH_STORAGE_LEVEL_CE = 1
```

表示密钥仅在首次解锁后可访问。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HuksAuthStorageLevel-HUKS_AUTH_STORAGE_LEVEL_CE = 1--><!--Device-HuksAuthStorageLevel-HUKS_AUTH_STORAGE_LEVEL_CE = 1-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本11：SystemCapability.Security.Huks.Extension

## HUKS_AUTH_STORAGE_LEVEL_ECE

```TypeScript
HUKS_AUTH_STORAGE_LEVEL_ECE = 2
```

表示密钥仅在解锁状态时可访问。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HuksAuthStorageLevel-HUKS_AUTH_STORAGE_LEVEL_ECE = 2--><!--Device-HuksAuthStorageLevel-HUKS_AUTH_STORAGE_LEVEL_ECE = 2-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本11：SystemCapability.Security.Huks.Extension

