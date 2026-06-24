# isApplicationDisableForbidden（系统接口）

## isApplicationDisableForbidden

```TypeScript
function isApplicationDisableForbidden(bundleName: string, userId: number, appIndex: number): boolean
```

��ͬ��������ѯָ���û���ָ��Ӧ�û����Ӧ���Ƿ����ý�ֹͣ�á�

**起始版本：** 24

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or (ohos.permission.GET_BUNDLE_INFO_PRIVILEGED and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS)

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ʾӦ�õİ����� |
| userId | number | 是 | ��ʾ�û�ID������ͨ��<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>��ȡ��ȡֵ��Χ�����ڵ���0�� |
| appIndex | number | 是 | ��ʾӦ��������ȡֵ��Χ0~5��ȡֵΪ0��ʾ��Ӧ�ã�ȡֵ1~5��ʾ����Ӧ�õ������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | ָ��Ӧ���Ƿ����ý�ֹͣ�á�<br/>����true��ʾָ��Ӧ���ѱ����ý�ֹͣ�ã�����false��ʾָ��Ӧ��û�б����ý�ֹͣ�á� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied. Non-system APP calling system API. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle is not found. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified user ID is not found. |
| [17700061](../../errorcode-universal.md#17700061-The) | The specified app index is invalid. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName: string = 'com.example.myapplication';
let userId: number = 100;
let appIndex: number = 0;

try {
  let data = bundleManager.isApplicationDisableForbidden(bundleName, userId, appIndex);
  hilog.info(0x0000, 'testTag', 'isApplicationDisableForbidden successfully: %{public}s', JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'isApplicationDisableForbidden failed: %{public}s', message);
}


```

