# getLaunchWantForBundleSync（系统接口）

## getLaunchWantForBundleSync

```TypeScript
function getLaunchWantForBundleSync(bundleName: string, userId?: number): Want
```

���ݸ����İ������û�ID����ȡ��������Ӧ�ó����Want������

**起始版本：** 24

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED, ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or (ohos.permission.GET_BUNDLE_INFO_PRIVILEGED and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS)

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ʾӦ�õİ����� |
| userId | number | 否 | ��ʾ�û�ID������ͨ��<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>��ȡ��<br/>Ĭ��ֵ�����÷������û���<br/>ȡֵ��Χ�����ڵ���0�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Want | Want���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api.&lt;br&gt;**适用版本：** 10 - 23 |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle is not found. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified user id is not found. |
| [17700026](../../errorcode-universal.md#17700026-The) | The specified bundle is disabled. |

**示例：**

```TypeScript
// 示例接口含有userId参数，获取用于启动指定用户下的应用程序所需的Want参数
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { Want } from '@kit.AbilityKit';

let bundleName = 'com.example.myapplication';
let userId = 100;

try {
  let want: Want = bundleManager.getLaunchWantForBundleSync(bundleName, userId);
  hilog.info(0x0000, 'testTag', 'getLaunchWantForBundleSync successfully. Data: %{public}s', JSON.stringify(want));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getLaunchWantForBundleSync failed. Cause: %{public}s', message);
}

```

```TypeScript
// 示例接口不含userId参数，获取用于启动当前用户下的应用程序所需的Want参数
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { Want } from '@kit.AbilityKit';

let bundleName = 'com.example.myapplication';

try {
  let want: Want = bundleManager.getLaunchWantForBundleSync(bundleName);
  hilog.info(0x0000, 'testTag', 'getLaunchWantForBundleSync successfully. Data: %{public}s', JSON.stringify(want));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getLaunchWantForBundleSync failed. Cause: %{public}s', message);
}

```

