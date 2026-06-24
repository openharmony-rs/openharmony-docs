# getApplicationLabel

## getApplicationLabel

```TypeScript
function getApplicationLabel(bundleName: string, appIndex: number): Promise<string>
```

��ȡָ�������ͷ���������Ӧ�����ơ�ʹ��Promise�첽�ص���

**起始版本：** 26.0.0

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ӧ�õİ����� |
| appIndex | number | 是 | ��ʾӦ��������ȡֵ��Χ0~5��ȡֵΪ0��ʾ��Ӧ�ã�ȡֵ1~5��ʾ����Ӧ�õ������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise���󣬵��óɹ�����Ӧ�����ƣ�����ʧ�ܷ��ش������ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle is not found. |
| [17700061](../../errorcode-universal.md#17700061-The) | The specified app index is invalid. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  bundleManager.getApplicationLabel('com.hap.myapplication', 1).then((data: string) => {
    hilog.info(0x0000, 'testTag', 'getApplicationLabel succeed: Data: %{public}s', data);
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getApplicationLabel failed: %{public}d  %{public}s', err.code, err.message);
  });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getApplicationLabel failed: error %{public}d  %{public}s', err.code, err.message);
}

```

