# Options

```TypeScript
interface Options
```

Represents the configuration of a **Preferences** instance.

**Since:** 10

<!--Device-preferences-interface Options--><!--Device-preferences-interface Options-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core

## Modules to Import

```TypeScript
import { preferences } from '@kit.ArkData';
```

## dataGroupId

```TypeScript
dataGroupId?: string | null | undefined
```

Application group ID. <!--RP1-->Currently, this parameter is not supported.<!--RP1End-->

This parameter is optional. A **Preferences** instance will be created in the sandbox path corresponding to the specified **dataGroupId**. If this parameter is not specified, the **Preferences** instance is created in the sandbox directory of the application.

This attribute can be used only in the stage model.

This API can be used in atomic services since API version 11.

**Type:** string &#124; null &#124; undefined

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Options-dataGroupId?: string | null | undefined--><!--Device-Options-dataGroupId?: string | null | undefined-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core

## name

```TypeScript
name: string
```

Name of the **Preferences** instance. It must be longer than 0 bytes and less than or equal to 255 bytes, and cannot contain or end with slashes (/).

This API can be used in atomic services since API version 11.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Options-name: string--><!--Device-Options-name: string-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core

## sharedMapSize

```TypeScript
sharedMapSize?: number
```

Initial cache file size, in KB. This parameter is optional. It indicates the initial inter-process shared cache file size of the current **Preferences** instance, and takes effect only when the storage mode is set to **GSKV**. The value can be 0 or within the range of [256, 1112784]. If this parameter is not specified, the system automatically initializes the cache file as needed. If this parameter is set to 0, the initial cache file size is 0, the cache file of this **Preferences** instance will not grow, and this **Preferences** instance does not support cross-process access. If this parameter is set to a valid value greater than 0, the initial cache file size is the configured value, and the cache file size of this **Preferences** instance will still grow as needed. The configuration value can be dynamically switched when the **Preferences** instance is disconnected and reconnected. Unit: kb. Value constraint: The value can be 0. Value range: [256,1112784]. Default value: 1112784.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-Options-sharedMapSize?: long--><!--Device-Options-sharedMapSize?: long-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core

## storageType

```TypeScript
storageType?: StorageType | null | undefined
```

Storage mode to be used by the **Preferences** instance. This parameter is optional. If this parameter is left blank, the XML storage type is used by default. After the storage type is set for a **Preferences** instance, it cannot be changed.

This API can be used in atomic services since API version 18.

**Type:** [StorageType](arkts-arkdata-preferences-storagetype-e.md) &#124; null &#124; undefined

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-Options-storageType?: StorageType | null | undefined--><!--Device-Options-storageType?: StorageType | null | undefined-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core
