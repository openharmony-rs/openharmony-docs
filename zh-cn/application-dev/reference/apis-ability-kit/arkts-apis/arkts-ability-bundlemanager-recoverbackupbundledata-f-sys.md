# recoverBackupBundleData（系统接口）

## recoverBackupBundleData

```TypeScript
function recoverBackupBundleData(bundleName: string, userId: number, appIndex: number): Promise<void>
```

�ָ�ָ���û���ָ��Ӧ�û����Ӧ�õı������ݡ�ʹ��Promise�첽�ص���

**起始版本：** 21

**需要权限：** ohos.permission.RECOVER_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ҫ�ָ����ݵ�Ӧ�ð����� |
| userId | number | 是 | ��ʾ�û�ID������ͨ��<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>��ȡ��ȡֵ��Χ�����ڵ���0�� |
| appIndex | number | 是 | ��ʾӦ��������ȡֵ��Χ0~5��ȡֵΪ0��ʾ��Ӧ�ã�ȡֵ1~5��ʾ����Ӧ�õ������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified user ID is not found. |
| [17700061](../../errorcode-universal.md#17700061-AppIndex) | AppIndex not in valid range. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// 请开发者替换为实际的包名、用户ID和应用索引
let bundleName: string = 'com.ohos.demo';
let userId: number = 100;
let appIndex: number = 0;

try {
  bundleManager.recoverBackupBundleData(bundleName, userId, appIndex).then(() => {
    hilog.info(0x0000, 'testTag', 'recoverBackupBundleData successfully');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'recoverBackupBundleData failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'recoverBackupBundleData failed. Cause: %{public}s', message);
}

```

