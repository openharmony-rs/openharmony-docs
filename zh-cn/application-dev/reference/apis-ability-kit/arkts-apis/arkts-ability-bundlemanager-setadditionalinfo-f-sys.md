# setAdditionalInfo（系统接口）

## setAdditionalInfo

```TypeScript
function setAdditionalInfo(bundleName: string, additionalInfo: string): void
```

����ָ��Ӧ�õĶ�����Ϣ���˽ӿڽ���Ӧ���г����á�

**起始版本：** 11

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ָ��Ӧ�õİ����� |
| additionalInfo | string | 是 | ��Ҫ���õ�Ӧ�õĶ�����Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter bundleName is empty. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700053](../../errorcode-universal.md#17700053-The) | The caller is not AppGallery. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";
let additionalInfo = "xxxxxxxxx,formUpdateLevel:4";

try {
  bundleManager.setAdditionalInfo(bundleName, additionalInfo);
  hilog.info(0x0000, 'testTag', 'setAdditionalInfo successfully.');
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'setAdditionalInfo failed. Cause: %{public}s', message);
}

```

