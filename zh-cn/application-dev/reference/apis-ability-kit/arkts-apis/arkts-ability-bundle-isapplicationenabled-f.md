# isApplicationEnabled

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

## isApplicationEnabled

```TypeScript
function isApplicationEnabled(bundleName: string, callback: AsyncCallback<boolean>): void
```

根据给定的bundleName查询指定应用程序是否已经启用，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

<!--Device-bundle-function isApplicationEnabled(bundleName: string, callback: AsyncCallback<boolean>): void--><!--Device-bundle-function isApplicationEnabled(bundleName: string, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要查询的应用Bundle名称。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 回调函数，返回boolean代表是否启用。 |

**示例**

```TypeScript
import bundle from '@ohos.bundle';

let bundleName: string = "com.example.myapplication";

bundle.isApplicationEnabled(bundleName, (err, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. Data:' + JSON.stringify(data));
})
```


## isApplicationEnabled

```TypeScript
function isApplicationEnabled(bundleName: string): Promise<boolean>
```

根据给定的bundleName查询指定应用程序是否已经启用，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

<!--Device-bundle-function isApplicationEnabled(bundleName: string): Promise<boolean>--><!--Device-bundle-function isApplicationEnabled(bundleName: string): Promise<boolean>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要查询的应用Bundle名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise形式返回boolean代表是否启用。 |

**示例**

```TypeScript
import bundle from '@ohos.bundle';
import { BusinessError } from '@ohos.base';

let bundleName: string = "com.example.myapplication";

bundle.isApplicationEnabled(bundleName)
  .then((data) => {
    console.info('Operation successful. Data: ' + JSON.stringify(data));
  }).catch((error: BusinessError) => {
    console.error('Operation failed. Cause: ' + JSON.stringify(error));
  })
```

