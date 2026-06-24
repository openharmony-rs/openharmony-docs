# enableDynamicIcon（系统接口）

## enableDynamicIcon

```TypeScript
function enableDynamicIcon(bundleName: string, moduleName: string): Promise<void>
```

���ݸ�����bundleName��moduleNameʹ�ܶ�̬ͼ�ꡣʹ��Promise�첽�ص���

**起始版本：** 12

**需要权限：** ohos.permission.ACCESS_DYNAMIC_ICON

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ҫʹ�ܶ�̬ͼ���Ӧ�����ơ� |
| moduleName | string | 是 | Ҫʹ�ܶ�̬ͼ���ģ�����ơ� |

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
| [17700002](../../errorcode-universal.md#17700002-The) | The specified moduleName is not found. |
| [17700304](../../errorcode-universal.md#17700304-Failed) | Failed to enable the dynamic icon. |
| [17700307](../../errorcode-universal.md#17700307-Dynamic) | Dynamic icons cannot take effect due to existing custom themes.&lt;br&gt;**适用版本：** 20+ |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName: string = 'com.ohos.demo';
let moduleName: string = 'moduleTest';

try {
  bundleManager.enableDynamicIcon(bundleName, moduleName).then((data) => {
    hilog.info(0x0000, 'testTag', 'enableDynamicIcon successfully');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'enableDynamicIcon failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'enableDynamicIcon failed. Cause: %{public}s', message);
}

```


## enableDynamicIcon

```TypeScript
function enableDynamicIcon(bundleName: string, moduleName: string, option?: BundleOptions): Promise<void>
```

���ݸ�����bundleName��moduleName��optionʹ�ܶ�̬ͼ�ꡣʹ��Promise�첽�ص���

ʹ�ܵ�ǰ�û��µĶ�̬ͼ����Ϣʱ��Ҫ����Ȩ��ohos.permission.ACCESS_DYNAMIC_ICON��

ʹ�������û��µĶ�̬ͼ����Ϣʱ��Ҫ����Ȩ��ohos.permission.ACCESS_DYNAMIC_ICON �� ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS��

**起始版本：** 20

**需要权限：** ohos.permission.ACCESS_DYNAMIC_ICON or (ohos.permission.ACCESS_DYNAMIC_ICON and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS)

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ҫʹ�ܶ�̬ͼ���Ӧ�ð����� |
| moduleName | string | 是 | Ҫʹ�ܶ�̬ͼ���ģ������ |
| option | BundleOptions | 否 | ָ����Ҫʹ�ܶ�̬ͼ����û��ͷ���������ȱʡʱʹ��Ӧ�������û������з����Ķ�̬ͼ�ꡣ |

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
| [17700002](../../errorcode-universal.md#17700002-The) | The specified moduleName is not found. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified user ID is not found. |
| [17700061](../../errorcode-universal.md#17700061-AppIndex) | AppIndex not in valid range. |
| [17700304](../../errorcode-universal.md#17700304-Failed) | Failed to enable the dynamic icon. |
| [17700307](../../errorcode-universal.md#17700307-Dynamic) | Dynamic icons cannot take effect due to existing custom themes. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName: string = 'com.ohos.demo';
let moduleName: string = 'moduleTest';
let option: bundleManager.BundleOptions = { 'userId': 100, 'appIndex': 0 };

try {
  bundleManager.enableDynamicIcon(bundleName, moduleName, option).then(() => {
    hilog.info(0x0000, 'testTag', 'enableDynamicIcon successfully');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'enableDynamicIcon failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'enableDynamicIcon failed. Cause: %{public}s', message);
}

```

