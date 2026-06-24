# getSharedBundleInfo（系统接口）

## getSharedBundleInfo

```TypeScript
function getSharedBundleInfo(bundleName: string,  moduleName: string, callback: AsyncCallback<Array<SharedBundleInfo>>): void
```

��ȡָ���Ĺ�������Ϣ��ʹ��callback�첽�ص���

��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�

**起始版本：** 10

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ʾӦ�ó����bundleName�� |
| moduleName | string | 是 | ��ʾ����ѯ��module��name�� |
| callback | AsyncCallback&lt;Array&lt;SharedBundleInfo&gt;&gt; | 是 | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)������ȡ�ɹ�ʱ<br/>��errΪundefined��dataΪ��ȡ��ָ����������Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700002](../../errorcode-universal.md#17700002-The) | The specified moduleName is not found. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';
let moduleName = 'library';

try {
  bundleManager.getSharedBundleInfo(bundleName, moduleName, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getSharedBundleInfo failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'getSharedBundleInfo successfully: %{public}s', JSON.stringify(data));
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getSharedBundleInfo failed: %{public}s', message);
}

```


## getSharedBundleInfo

```TypeScript
function getSharedBundleInfo(bundleName: string, moduleName: string): Promise<Array<SharedBundleInfo>>
```

��ȡָ���Ĺ�������Ϣ��ʹ��Promise�첽�ص���

��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�

**起始版本：** 10

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ʾӦ�ó����bundleName�� |
| moduleName | string | 是 | ��ʾ����ѯ��module��name�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;SharedBundleInfo&gt;&gt; | Promise���󣬷���ָ���Ĺ�������Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700002](../../errorcode-universal.md#17700002-The) | The specified moduleName is not found. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';
let moduleName = 'library';

try {
  bundleManager.getSharedBundleInfo(bundleName, moduleName).then((data) => {
    hilog.info(0x0000, 'testTag', 'getSharedBundleInfo successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getSharedBundleInfo failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getSharedBundleInfo failed. Cause: %{public}s', message);
}

```

