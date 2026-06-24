# getLaunchWantForBundle（系统接口）

## getLaunchWantForBundle

```TypeScript
function getLaunchWantForBundle(bundleName: string, userId: number, callback: AsyncCallback<Want>): void
```

���ݸ�����bundleName��userId��ȡ��������Ӧ�ó����Want������ʹ��callback�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ʾӦ�ó����bundleName�� |
| userId | number | 是 | ��ʾ�û�ID������ͨ��<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>��ȡ�� |
| callback | AsyncCallback&lt;Want&gt; | 是 | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)������ȡ�ɹ�ʱ��errΪundefined��data<br/>Ϊ��ȡ����Want������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Calling) | Calling interface without permission 'ohos.permission.GET_BUNDLE_INFO_PRIVILEGED'. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified user ID is not found. |
| [17700026](../../errorcode-universal.md#17700026-The) | The specified bundle is disabled. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';
let userId = 100;

try {
  bundleManager.getLaunchWantForBundle(bundleName, userId, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getLaunchWantForBundle failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'getLaunchWantForBundle successfully: %{public}s', JSON.stringify(data));
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getLaunchWantForBundle failed: %{public}s', message);
}

```


## getLaunchWantForBundle

```TypeScript
function getLaunchWantForBundle(bundleName: string, callback: AsyncCallback<Want>): void
```

���ݸ�����bundleName��ȡ��������Ӧ�ó����Want������ʹ��callback�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ʾӦ�ó����bundleName�� |
| callback | AsyncCallback&lt;Want&gt; | 是 | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)������ȡ�ɹ�ʱ��errΪundefined��data<br/>Ϊ��ȡ����Want������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Calling) | Calling interface without permission 'ohos.permission.GET_BUNDLE_INFO_PRIVILEGED'. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700026](../../errorcode-universal.md#17700026-The) | The specified bundle is disabled. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';

try {
  bundleManager.getLaunchWantForBundle(bundleName, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getLaunchWantForBundle failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'getLaunchWantForBundle successfully: %{public}s', JSON.stringify(data));
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getLaunchWantForBundle failed: %{public}s', message);
}

```


## getLaunchWantForBundle

```TypeScript
function getLaunchWantForBundle(bundleName: string, userId?: number): Promise<Want>
```

���ݸ�����bundleName��userId��ȡ��������Ӧ�ó����Want������ʹ��Promise�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ʾӦ�ó����bundleName�� |
| userId | number | 否 | ��ʾ�û�ID������ͨ��<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>��ȡ��Ĭ��ֵ�����÷������û���ȡֵ��Χ�����ڵ���0�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Want&gt; | Promise���󣬷���Want���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Calling) | Calling interface without permission 'ohos.permission.GET_BUNDLE_INFO_PRIVILEGED'. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified user ID is not found. |
| [17700026](../../errorcode-universal.md#17700026-The) | The specified bundle is disabled. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';
let userId = 100;

try {
  bundleManager.getLaunchWantForBundle(bundleName, userId).then((data) => {
    hilog.info(0x0000, 'testTag', 'getLaunchWantForBundle successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getLaunchWantForBundle failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getLaunchWantForBundle failed. Cause: %{public}s', message);
}

```

