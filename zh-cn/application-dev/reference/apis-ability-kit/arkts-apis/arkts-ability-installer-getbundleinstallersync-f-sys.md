# getBundleInstallerSync（系统接口）

## 导入模块

```TypeScript
import { installer } from '@kit.AbilityKit';
```

<a id="getbundleinstallersync"></a>
## getBundleInstallerSync

```TypeScript
function getBundleInstallerSync(): BundleInstaller
```

获取并返回BundleInstaller对象。

**起始版本：** 10

<!--Device-installer-function getBundleInstallerSync(): BundleInstaller--><!--Device-installer-function getBundleInstallerSync(): BundleInstaller-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BundleInstaller](arkts-ability-installer-bundleinstaller-i-sys.md) | BundleInstaller object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

