# isApplicationEnabled（系统接口）

## isApplicationEnabled

```TypeScript
function isApplicationEnabled(bundleName: string, appIndex: number): Promise<boolean>
```

��ȡָ��Ӧ�û����Ӧ�õĽ��û�ʹ��״̬��ʹ��Promise�첽�ص���

**起始版本：** 12

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ʾӦ�ó����bundleName�� |
| appIndex | number | 是 | ��ʾ����Ӧ�õ�������<br/>appIndexΪ0ʱ����ʾ��ȡ��Ӧ�õĽ��û�ʹ��״̬��appIndex����0ʱ����ʾ��ȡָ������Ӧ�õĽ��û�ʹ��״̬�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise���󣬷���true��ʾ��ǰӦ��Ϊʹ��״̬������false��ʾ��ǰӦ��Ϊ����״̬�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700061](../../errorcode-universal.md#17700061-AppIndex) | AppIndex not in valid range. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';

try {
  bundleManager.isApplicationEnabled(bundleName, 1).then((data) => {
    hilog.info(0x0000, 'testTag', 'isApplicationEnabled successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'isApplicationEnabled failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'isApplicationEnabled failed. Cause: %{public}s', message);
}

```


## isApplicationEnabled

```TypeScript
function isApplicationEnabled(bundleName: string, callback: AsyncCallback<boolean>): void
```

��ȡָ��Ӧ�õĽ��û�ʹ��״̬��ʹ��callback�첽�ص���

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ʾӦ�ó����bundleName�� |
| callback | AsyncCallback&lt;boolean&gt; | 是 | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)������true��ʾ��ǰӦ��Ϊʹ��״̬������<br/>false��ʾӦ��Ϊ����״̬�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';

try {
  bundleManager.isApplicationEnabled(bundleName, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'isApplicationEnabled failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'isApplicationEnabled successfully: %{public}s', JSON.stringify(data));
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'isApplicationEnabled failed: %{public}s', message);
}

```


## isApplicationEnabled

```TypeScript
function isApplicationEnabled(bundleName: string): Promise<boolean>
```

��ȡָ��Ӧ�õĽ��û�ʹ��״̬��ʹ��Promise�첽�ص���

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ʾӦ�ó����bundleName�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise���󣬷���true��ʾ��ǰӦ��Ϊʹ��״̬������false��ʾ��ǰӦ��Ϊ����״̬�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';

try {
  bundleManager.isApplicationEnabled(bundleName).then((data) => {
    hilog.info(0x0000, 'testTag', 'isApplicationEnabled successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'isApplicationEnabled failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'isApplicationEnabled failed. Cause: %{public}s', message);
}

```

