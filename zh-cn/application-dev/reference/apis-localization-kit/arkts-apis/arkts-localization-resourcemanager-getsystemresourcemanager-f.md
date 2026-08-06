# getSystemResourceManager

## getSystemResourceManager

```TypeScript
export function getSystemResourceManager(): ResourceManager
```

获取系统资源管理对象，用于访问系统预置的资源。 > **说明** > > 该接口获取到的系统资源管理ResourceManager对象中的Configuration为默认值。默认值如下：{"locale": "", "direction": -1, "deviceType": -1, " > screenDensity": 0, "colorMode": 1, "mcc": 0, "mnc": 0}。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 20

**替代接口：** [resourceManager.getSysResourceManager](arkts-localization-resourcemanager-getsysresourcemanager-f.md#getsysresourcemanager)

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-resourceManager-export function getSystemResourceManager(): ResourceManager--><!--Device-resourceManager-export function getSystemResourceManager(): ResourceManager-End-->

**系统能力：** SystemCapability.Global.ResourceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 系统资源管理对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9001009](../errorcode-resource-manager.md#9001009-获取系统资源管理对象失败) | Failed to access the system resource.which is not mapped to application sandbox, This error code will be thrown. |

**示例：**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let systemResourceManager = resourceManager.getSystemResourceManager();
  systemResourceManager.getStringValue($r('sys.string.ohos_lab_vibrate').id).then((value: string) => {
    let str = value;
  }).catch((error: BusinessError) => {
    console.error("systemResourceManager getStringValue promise error is " + error);
  });
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getSystemResourceManager failed, error code: ${code}, message: ${message}.`);
}
```

