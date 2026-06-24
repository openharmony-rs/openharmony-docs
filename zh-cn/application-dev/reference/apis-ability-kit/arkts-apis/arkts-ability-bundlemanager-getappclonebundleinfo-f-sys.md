# getAppCloneBundleInfo（系统接口）

## getAppCloneBundleInfo

```TypeScript
function getAppCloneBundleInfo(bundleName: string, appIndex: number, bundleFlags: number, userId?: number): Promise<BundleInfo>
```

����bundleName������������[bundleFlags](arkts-ability-bundlemanager-bundleflag-e.md#BundleFlag)�Լ��û�ID��ѯ��Ӧ�û����Ӧ�õ�
BundleInfo��ʹ��Promise�첽�ص���

��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�

**起始版本：** 12

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ʾҪ��ѯ��Ӧ��Bundle���ơ� |
| appIndex | number | 是 | ��ʾҪ��ѯ�ķ���Ӧ��������<br/>appIndexΪ0ʱ����ʾ��ѯ��Ӧ����Ϣ��appIndex����0ʱ����ʾ��ѯָ������Ӧ����Ϣ�� |
| bundleFlags | number | 是 | ��ʾ����ָ��Ҫ���ص�BundleInfo�����а�������Ϣ�ı�־�� |
| userId | number | 否 | ��ʾ�û�ID������ͨ��<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>��ȡ��Ĭ��ֵ�����÷������û���ȡֵ��Χ�����ڵ���0�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;BundleInfo&gt; | Promise���󡣷���Ӧ�ð���Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified user ID is not found. |
| [17700026](../../errorcode-universal.md#17700026-The) | The specified bundle is disabled. |
| [17700061](../../errorcode-universal.md#17700061-AppIndex) | AppIndex not in valid range. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';
let appIndex = 1;
let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_HAP_MODULE |
bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY;

try {
  bundleManager.getAppCloneBundleInfo(bundleName, appIndex, bundleFlags).then((res: bundleManager.BundleInfo) => {
    hilog.info(0x0000, 'testTag', 'getAppCloneBundleInfo res: BundleInfo = %{public}s', JSON.stringify(res));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAppCloneBundleInfo failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAppCloneBundleInfo failed. Cause: %{public}s', message);
}

```

