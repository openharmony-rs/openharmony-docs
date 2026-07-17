# getAppCloneIdentityBySandboxDataDir（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getAppCloneIdentityBySandboxDataDir

```TypeScript
function getAppCloneIdentityBySandboxDataDir(sandboxDataDir: string): AppCloneIdentity
```

根据应用的沙箱目录名称获取应用的身份信息，包括应用包名和分身索引信息。

**起始版本：** 20

<!--Device-bundleManager-function getAppCloneIdentityBySandboxDataDir(sandboxDataDir: string): AppCloneIdentity--><!--Device-bundleManager-function getAppCloneIdentityBySandboxDataDir(sandboxDataDir: string): AppCloneIdentity-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sandboxDataDir | string | 是 | 表示[应用的沙箱目录](../../../../file-management/app-sandbox-directory.md)名称。 <br>**说明：**<br> 参数不校验合法性，如果入参sandboxDataDir不符合分身应用或元服务的目录名称格式，则sandboxDataDir将作为返回信息中的AppCloneIdentity.bundleName返回，此时AppCloneIdentity.appIndex为0。 <br> 1.分身应用目录名称格式要求：`+clone-{appIndex}+{bundleName}`，appIndex和bundleName是变量，对应分身索引和应用包名，例如： `+clone-1+com.example.myapplication`。<br> 2.元服务目录名称格式格式要求：`+auid-{uid}+{bundleName}`，uid和bundleName是变量，对应应用程序的UID和应用包名，例如： `+auid-20000000+com.example.myapplication`。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AppCloneIdentity](arkts-ability-bundlemanager-appcloneidentity-t.md) | 返回应用包名和分身索引信息。 |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// 主应用
let dataDir = 'com.example.myapplication';
try {
  let res = bundleManager.getAppCloneIdentityBySandboxDataDir(dataDir);
  hilog.info(0x0000, 'testTag', 'getAppCloneIdentityBySandboxDataDir successfully. res:%{public}s',
    JSON.stringify(res));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAppCloneIdentityBySandboxDataDir failed. Cause: %{public}s',
    message);
}

// 分身应用
let cloneDataDir = '+clone-1+com.example.myapplication';
try {
  let res = bundleManager.getAppCloneIdentityBySandboxDataDir(cloneDataDir);
  hilog.info(0x0000, 'testTag', 'getAppCloneIdentityBySandboxDataDir successfully. res:%{public}s',
    JSON.stringify(res));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAppCloneIdentityBySandboxDataDir failed. Cause: %{public}s',
    message);
}

// 原子化服务
let atomicDataDir = '+auid-20000000+com.example.myapplication';
try {
  let res = bundleManager.getAppCloneIdentityBySandboxDataDir(atomicDataDir);
  hilog.info(0x0000, 'testTag', 'getAppCloneIdentityBySandboxDataDir successfully. res:%{public}s',
    JSON.stringify(res));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAppCloneIdentityBySandboxDataDir failed. Cause: %{public}s',
    message);
}

```

