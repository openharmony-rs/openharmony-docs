# getSignatureInfo

## getSignatureInfo

```TypeScript
function getSignatureInfo(uid: number): SignatureInfo
```

���ݸ�����uid��ȡ��ӦӦ�õ�[ǩ����Ϣ](bundleManager/BundleInfo:SignatureInfo)��

**起始版本：** 18

**需要权限：** ohos.permission.GET_SIGNATURE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | number | 是 | ��ʾӦ�ó����UID�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SignatureInfo | ����SignatureInfo���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [17700021](../../errorcode-universal.md#17700021-The) | The uid is not found. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let uid = 20010005; // uid需要替换为对应应用程序的UID。
try {
  let data = bundleManager.getSignatureInfo(uid);
  hilog.info(0x0000, 'testTag', 'getSignatureInfo successfully. Data: %{public}s', JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getSignatureInfo failed. Cause: %{public}s', message);
}

```

