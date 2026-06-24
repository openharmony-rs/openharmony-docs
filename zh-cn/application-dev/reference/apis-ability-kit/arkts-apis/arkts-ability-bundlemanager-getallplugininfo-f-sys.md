# getAllPluginInfo（系统接口）

## getAllPluginInfo

```TypeScript
function getAllPluginInfo(hostBundleName: string, userId?: number): Promise<Array<PluginBundleInfo>>
```

���ݸ�����hostBundleName��userId��ȡ���е�PluginBundleInfo��ʹ��Promise�첽�ص���

**起始版本：** 19

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hostBundleName | string | 是 | ��ʾ��װ�����Ӧ�ð����� |
| userId | number | 否 | ��ʾ�û�ID������ͨ��<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>��ȡ��Ĭ��ֵ�����÷������û�ID��ȡֵ��Χ�����ڵ���0�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;PluginBundleInfo&gt;&gt; | Promise���󣬷���Array�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified user ID is not found. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let hostBundleName = 'com.ohos.demo';
let userId = 100;

try {
  bundleManager.getAllPluginInfo(hostBundleName, userId).then((data) => {
    hilog.info(0x0000, 'testTag', 'getAllPluginInfo successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAllPluginInfo failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllPluginInfo failed. Cause: %{public}s', message);
}

```

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let hostBundleName = 'com.ohos.demo';

try {
  bundleManager.getAllPluginInfo(hostBundleName).then((data) => {
    hilog.info(0x0000, 'testTag', 'getAllPluginInfo successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAllPluginInfo failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllPluginInfo failed. Cause: %{public}s', message);
}

```

