# getInstalledBundleList

## getInstalledBundleList

```TypeScript
function getInstalledBundleList(bundleFlags: number): Promise<Array<BundleInfo>>
```

���ݸ�����bundleFlags��ȡϵͳ�����е�BundleInfo��ʹ��Promise�첽�ص���

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_GET_INSTALLED_BUNDLE_LIST

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleFlags | number | 是 | ָ�����ص�BundleInfo����������Ϣ��������ο�<br/>[BundleFlag](arkts-ability-bundlemanager-bundleflag-e.md#BundleFlag)�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;BundleInfo&gt;&gt; | Promise���󣬷��ص�ǰ�Ѱ�װӦ�õ���Ϣ�б��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_DEFAULT;

try {
  bundleManager.getInstalledBundleList(bundleFlags).then((data) => {
    hilog.info(0x0000, 'testTag', 'getInstalledBundleList successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getInstalledBundleList failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getInstalledBundleList failed. Cause: %{public}s', message);
}

```

