# disableDynamicIcon（系统接口）

## disableDynamicIcon

```TypeScript
function disableDynamicIcon(bundleName: string): Promise<void>
```

���ݸ�����bundleName���ö�̬ͼ�ꡣʹ��Promise�첽�ص���

**起始版本：** 12

**需要权限：** ohos.permission.ACCESS_DYNAMIC_ICON

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ҫ���ö�̬ͼ���Ӧ�����ơ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700305](../../errorcode-universal.md#17700305-Failed) | Failed to disable the dynamic icon. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName: string = 'com.ohos.demo';

try {
  bundleManager.disableDynamicIcon(bundleName).then((data) => {
    hilog.info(0x0000, 'testTag', 'disableDynamicIcon successfully');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'disableDynamicIcon failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'disableDynamicIcon failed. Cause: %{public}s', message);
}

```


## disableDynamicIcon

```TypeScript
function disableDynamicIcon(bundleName: string, option?: BundleOptions): Promise<void>
```

���ݸ�����bundleName��option���ö�̬ͼ�ꡣʹ��Promise�첽�ص���

���õ�ǰ�û��µĶ�̬ͼ����Ϣʱ��Ҫ����Ȩ��ohos.permission.ACCESS_DYNAMIC_ICON��

���������û��µĶ�̬ͼ����Ϣʱ��Ҫ����Ȩ��ohos.permission.ACCESS_DYNAMIC_ICON �� ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS��

**起始版本：** 20

**需要权限：** ohos.permission.ACCESS_DYNAMIC_ICON or (ohos.permission.ACCESS_DYNAMIC_ICON and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS)

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ҫ���ö�̬ͼ���Ӧ�ð����� |
| option | BundleOptions | 否 | ָ����Ҫ���ö�̬ͼ����û��ͷ���������ȱʡʱ����Ӧ�������û������з����Ķ�̬ͼ�ꡣ |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified user ID is not found. |
| [17700061](../../errorcode-universal.md#17700061-AppIndex) | AppIndex not in valid range. |
| [17700305](../../errorcode-universal.md#17700305-Failed) | Failed to disable the dynamic icon. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName: string = 'com.ohos.demo';
let option: bundleManager.BundleOptions = { 'userId': 100, 'appIndex': 0 };

try {
  bundleManager.disableDynamicIcon(bundleName, option).then(() => {
    hilog.info(0x0000, 'testTag', 'disableDynamicIcon successfully');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'disableDynamicIcon failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'disableDynamicIcon failed. Cause: %{public}s', message);
}

```

