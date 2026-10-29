# BundleInfo (System API)

```TypeScript
interface BundleInfo
```

Defines the device-cloud synergy application information.

**Since:** 26.0.0

<!--Device-cloudData-interface BundleInfo--><!--Device-cloudData-interface BundleInfo-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the application.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleInfo-bundleName: string--><!--Device-BundleInfo-bundleName: string-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

## storeId

```TypeScript
storeId?: string
```

Name of the RDB store. The default value is an empty string. If the default value is used, this API queries all databases of this application.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleInfo-storeId?: string--><!--Device-BundleInfo-storeId?: string-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.
