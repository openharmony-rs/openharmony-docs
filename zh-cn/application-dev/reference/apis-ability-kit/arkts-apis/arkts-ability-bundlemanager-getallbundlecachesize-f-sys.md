# getAllBundleCacheSize（系统接口）

## getAllBundleCacheSize

```TypeScript
function getAllBundleCacheSize(): Promise<number>
```

��ȡȫ�ֻ����С����λ���ֽڡ�ʹ��Promise�첽�ص���

�г�������ʱ��Ӧ�õĻ��桢������[Ӧ������ָ��](../../../../../device-dev/subsystems/subsys-app-privilege-config-guide.md)�������á�
AllowAppDataNotCleared����Ȩ��Ӧ�õĻ��棬�޷�����ȡ��

**起始版本：** 15

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise���󡣷���ȫ�ֻ����С�����ֽ�Ϊ��λ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  bundleManager.getAllBundleCacheSize().then((data) => {
    hilog.info(0x0000, 'testTag', 'getAllBundleCacheSize successful. Data: ' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAllBundleCacheSize failed: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllBundleCacheSize failed: %{public}s', message);
}

```

