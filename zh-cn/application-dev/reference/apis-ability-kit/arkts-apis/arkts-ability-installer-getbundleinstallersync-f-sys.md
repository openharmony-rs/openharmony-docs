# getBundleInstallerSync（系统接口）

## getBundleInstallerSync

```TypeScript
function getBundleInstallerSync(): BundleInstaller
```

获取并返回BundleInstaller对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-installer-function getBundleInstallerSync(): BundleInstaller--><!--Device-installer-function getBundleInstallerSync(): BundleInstaller-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| BundleInstaller | BundleInstaller object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## 示例

```TypeScript
import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    installer.getBundleInstallerSync();
    console.info('getBundleInstallerSync successfully.');
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('getBundleInstallerSync failed. Cause: ' + message);
}
```

