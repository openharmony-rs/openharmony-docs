# BundleOptions

> **说明：** > > 从API version 7开始支持，从API version 9开始废弃，暂无替代接口。 查询选项，包含userId。

**起始版本：** 7

**废弃版本：** 9

<!--Device-bundle-export interface BundleOptions--><!--Device-bundle-export interface BundleOptions-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## 导入模块

```TypeScript
import { appControl } from '@kit.AbilityKit';
import { bundleManager } from '@kit.AbilityKit';
import { bundleMonitor } from '@kit.AbilityKit';
import { bundleResourceManager } from '@kit.AbilityKit';
import { bundle } from '@kit.AbilityKit';
import { defaultAppManager } from '@kit.AbilityKit';
import { distributedBundleManager } from '@kit.AbilityKit';
import { freeInstall } from '@kit.AbilityKit';
import { innerBundleManager, BundleStatusCallback } from '@kit.AbilityKit';
import { installer } from '@kit.AbilityKit';
import { launcherBundleManager } from '@kit.AbilityKit';
import { overlay } from '@kit.AbilityKit';
import { shortcutManager } from '@kit.AbilityKit';
import { skillManager } from '@kit.AbilityKit';
import { appDomainVerify } from '@kit.AbilityKit';
import { pluginBundleManager } from '@kit.AbilityKit';
```

## userId

```TypeScript
userId?: number
```

用户ID。默认值：调用方所在用户，取值范围：大于等于0。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

<!--Device-BundleOptions-userId?: number--><!--Device-BundleOptions-userId?: number-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

