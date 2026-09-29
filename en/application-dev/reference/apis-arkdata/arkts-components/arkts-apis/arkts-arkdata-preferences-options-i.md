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

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

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

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Options-name: string--><!--Device-Options-name: string-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core

## storageType

```TypeScript
storageType?: StorageType | null | undefined
```

Storage mode to be used by the **Preferences** instance. This parameter is optional. If this parameter is left blank, the XML storage type is used by default. After the storage type is set for a **Preferences** instance, it cannot be changed.

This API can be used in atomic services since API version 18.

**Type:** [StorageType](arkts-arkdata-preferences-storagetype-e.md) &#124; null &#124; undefined

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-Options-storageType?: StorageType | null | undefined--><!--Device-Options-storageType?: StorageType | null | undefined-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core
