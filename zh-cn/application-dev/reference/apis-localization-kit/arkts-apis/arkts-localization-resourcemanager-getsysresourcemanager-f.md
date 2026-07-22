# getSysResourceManager

## 导入模块

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
```

## getSysResourceManager

```TypeScript
export function getSysResourceManager(): ResourceManager
```

获取系统资源管理对象。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-resourceManager-export function getSysResourceManager(): ResourceManager--><!--Device-resourceManager-export function getSysResourceManager(): ResourceManager-End-->

**系统能力：** SystemCapability.Global.ResourceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ResourceManager](arkts-localization-resourcemanager-resourcemanager-i.md) | 系统资源管理对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9001009](../errorcode-resource-manager.md#9001009-获取系统资源管理对象失败) | Failed to access the system resource.which is not mapped to application sandbox, This error code will be thrown. |

**示例：**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let systemResourceManager = resourceManager.getSysResourceManager();
  // 'sys.string.ohos_lab_vibrate'仅作示例，请替换为实际使用的资源
  systemResourceManager.getStringValue($r('sys.string.ohos_lab_vibrate').id).then((value: string) => {
    let str = value;
  }).catch((error: BusinessError) => {
    console.error(`systemResourceManager getStringValue promise error: ${error}`);
  });
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getSysResourceManager failed, error code: ${code}, message: ${message}.`);
}

```

