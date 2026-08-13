# setHapModuleUpgradeFlag（系统接口）

## setHapModuleUpgradeFlag

```TypeScript
function setHapModuleUpgradeFlag(bundleName: string, 
    moduleName: string, upgradeFlag: UpgradeFlag, callback: AsyncCallback<void>): void
```

设置指定模块是否升级。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.INSTALL_BUNDLE

<!--Device-freeInstall-function setHapModuleUpgradeFlag(bundleName: string,     moduleName: string, upgradeFlag: UpgradeFlag, callback: AsyncCallback<void>): void--><!--Device-freeInstall-function setHapModuleUpgradeFlag(bundleName: string,     moduleName: string, upgradeFlag: UpgradeFlag, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用Bundle名称。 |
| moduleName | string | 是 | 应用程序模块名称。 |
| upgradeFlag | [UpgradeFlag](arkts-ability-freeinstall-upgradeflag-e-sys.md) | 是 | 仅供内部系统使用标志位。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | [回调函数](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md#AsyncCallback)。当函数调用成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700002](../errorcode-bundle.md#17700002-指定的modulename不存在) | The specified module name is not found. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |

## 示例

```TypeScript
import { freeInstall } from '@kit.AbilityKit';

let bundleName = 'com.example.myapplication';
let moduleName = 'entry';
let upgradeFlag = freeInstall.UpgradeFlag.SINGLE_UPGRADE;
try {
  freeInstall.setHapModuleUpgradeFlag(bundleName, moduleName, upgradeFlag, err => {
    if (err) {
      console.error('Operation failed:' + JSON.stringify(err));
    } else {
      console.info('Operation succeed');
    }
  });
} catch (err) {
  console.error('Operation failed:' + JSON.stringify(err));
}
```


## setHapModuleUpgradeFlag

```TypeScript
function setHapModuleUpgradeFlag(bundleName: string, moduleName: string, upgradeFlag: UpgradeFlag): Promise<void>
```

设置指定模块是否升级。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.INSTALL_BUNDLE

<!--Device-freeInstall-function setHapModuleUpgradeFlag(bundleName: string, moduleName: string, upgradeFlag: UpgradeFlag): Promise<void>--><!--Device-freeInstall-function setHapModuleUpgradeFlag(bundleName: string, moduleName: string, upgradeFlag: UpgradeFlag): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用Bundle名称。 |
| moduleName | string | 是 | 应用程序模块名称。 |
| upgradeFlag | [UpgradeFlag](arkts-ability-freeinstall-upgradeflag-e-sys.md) | 是 | 仅供内部系统使用标志位。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700002](../errorcode-bundle.md#17700002-指定的modulename不存在) | The specified module name is not found. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |

## 示例

ArkTS-Dyn示例:

```TypeScript
import { freeInstall } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'com.example.myapplication';
let moduleName = 'entry';
let upgradeFlag = freeInstall.UpgradeFlag.SINGLE_UPGRADE;
try {
  freeInstall.setHapModuleUpgradeFlag(bundleName, moduleName, upgradeFlag).then(() => {
    console.info('Operation succeed')
  }).catch((err: BusinessError) => {
    console.error('Operation failed:' + JSON.stringify(err));
  });
} catch (err) {
  console.error('Operation failed:' + JSON.stringify(err));
}
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { freeInstall } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
// 开发者需根据实际工程更新bundleName和moduleName。
let bundleName = 'com.example.myapplication';
let moduleName = 'entry';
let upgradeFlag = freeInstall.UpgradeFlag.SINGLE_UPGRADE;
try {
  freeInstall.setHapModuleUpgradeFlag(bundleName, moduleName, upgradeFlag).then(() => {
    console.info('Operation succeed')
  }).catch((err: Error) => {
    console.error('Operation failed:' + JSON.stringify(err as BusinessError));
  });
} catch (err) {
  console.error('Operation failed:' + JSON.stringify(err));
}
```

