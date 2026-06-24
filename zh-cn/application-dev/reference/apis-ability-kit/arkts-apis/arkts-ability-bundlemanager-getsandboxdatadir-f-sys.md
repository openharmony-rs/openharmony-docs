# getSandboxDataDir（系统接口）

## getSandboxDataDir

```TypeScript
function getSandboxDataDir(bundleName: string, appIndex: number): string
```

����Ӧ�ð����ͷ���������ȡ��Ӧ��ɳ��Ŀ¼��

**起始版本：** 20

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ʾҪ��ѯ��Ӧ�ð�������ǰ�û����д�Ӧ�û��߷����ſɲ�ѯ�����򷵻ش�����17700001�� |
| appIndex | number | 是 | ��ʾӦ��������ȡֵ��Χ0~5��ȡֵΪ0��ʾ��Ӧ�ã�ȡֵ1~5��ʾ����Ӧ�õ������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | ����Ӧ�õ�ɳ��Ŀ¼�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700061](../../errorcode-universal.md#17700061-AppIndex) | AppIndex not in valid range. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';
let appIndex = 1;

try {
  let dataDir = bundleManager.getSandboxDataDir(bundleName, appIndex);
  hilog.info(0x0000, 'testTag', 'getSandboxDataDir successfully. dataDir:%{public}s', dataDir);
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getSandboxDataDir failed. Cause: %{public}s', message);
}

```

