# getApplicationInfoSync（系统接口）

## getApplicationInfoSync

```TypeScript
function getApplicationInfoSync(bundleName: string, applicationFlags: number, userId: number) : ApplicationInfo
```

��ͬ���������ݸ�����bundleName��applicationFlags��userId��ȡApplicationInfo��

��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ʾӦ�ó����bundleName�� |
| applicationFlags | number | 是 | ��ʾ����ָ�������ص�ApplicationInfo�����а�������Ϣ������ȡֵ����ͬ����ο�<br/>[ApplicationFlag](arkts-ability-bundlemanager-applicationflag-e-sys.md#ApplicationFlag)�� |
| userId | number | 是 | ��ʾ�û�ID������ͨ��<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>��ȡ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ApplicationInfo | ����ApplicationInfo���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
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
let applicationFlags = bundleManager.ApplicationFlag.GET_APPLICATION_INFO_DEFAULT;
let userId = 100;

try {
  let data = bundleManager.getApplicationInfoSync(bundleName, applicationFlags, userId);
  hilog.info(0x0000, 'testTag', 'getApplicationInfoSync successfully: %{public}s', JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getApplicationInfoSync failed: %{public}s', message);
}

```


## getApplicationInfoSync

```TypeScript
function getApplicationInfoSync(bundleName: string, applicationFlags: number) : ApplicationInfo
```

��ͬ���������ݸ�����bundleName��applicationFlags��ȡApplicationInfo��

��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ʾӦ�ó����bundleName�� |
| applicationFlags | number | 是 | ��ʾ����ָ�������ص�ApplicationInfo�����а�������Ϣ������ȡֵ����ͬ����ο�<br/>[ApplicationFlag](arkts-ability-bundlemanager-applicationflag-e-sys.md#ApplicationFlag)�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ApplicationInfo | ����ApplicationInfo���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
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
let applicationFlags = bundleManager.ApplicationFlag.GET_APPLICATION_INFO_DEFAULT;

try {
  let data = bundleManager.getApplicationInfoSync(bundleName, applicationFlags);
  hilog.info(0x0000, 'testTag', 'getApplicationInfoSync successfully: %{public}s', JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getApplicationInfoSync failed: %{public}s', message);
}

```

