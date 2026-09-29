# Options

```TypeScript
interface Options
```

Represents the configuration options of a **Preferences** instance.

**Since:** 12

<!--Device-sendablePreferences-interface Options--><!--Device-sendablePreferences-interface Options-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core

## Modules to Import

```TypeScript
import { sendablePreferences } from '@kit.ArkData';
```

## dataGroupId

```TypeScript
dataGroupId?: string | null
```

Application group ID. <!--RP1-->Currently, this parameter is not supported.<!--RP1End-->

This parameter is optional. A **Preferences** instance will be created in the sandbox path corresponding to the specified **dataGroupId**. If this parameter is not specified, the **Preferences** instance is created in the sandbox directory of the application.

This attribute can be used only in the stage model.

**Type:** string &#124; null

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-Options-dataGroupId?: string | null--><!--Device-Options-dataGroupId?: string | null-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core

## name

```TypeScript
name: string
```

Name of the **Preferences** instance.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-Options-name: string--><!--Device-Options-name: string-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core
