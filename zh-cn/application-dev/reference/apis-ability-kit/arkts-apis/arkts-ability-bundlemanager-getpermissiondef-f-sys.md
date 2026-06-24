# getPermissionDef（系统接口）

## getPermissionDef

```TypeScript
function getPermissionDef(permissionName: string, callback: AsyncCallback<PermissionDef>): void
```

���ݸ�����permissionName��ȡȨ�޶���ṹ��PermissionDef��Ϣ��ʹ��callback�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| permissionName | string | 是 | ��ʾȨ�����ơ� |
| callback | AsyncCallback&lt;PermissionDef&gt; | 是 | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)������ȡ�ɹ�ʱ��errΪ<br/>undefined��dataΪ��ȡ����Array������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700006](../../errorcode-universal.md#17700006-The) | The specified permission is not found. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let permission = "ohos.permission.GET_BUNDLE_INFO";
try {
  bundleManager.getPermissionDef(permission, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getPermissionDef failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'getPermissionDef successfully: %{public}s', JSON.stringify(data));
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getPermissionDef failed: %{public}s', message);
}

```


## getPermissionDef

```TypeScript
function getPermissionDef(permissionName: string): Promise<PermissionDef>
```

���ݸ�����permissionName��ȡȨ�޶���ṹ��PermissionDef��Ϣ��ʹ��Promise�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| permissionName | string | 是 | ��ʾȨ�޲������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PermissionDef&gt; | Promise���󣬷���Array���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700006](../../errorcode-universal.md#17700006-The) | The specified permission is not found. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let permissionName = "ohos.permission.GET_BUNDLE_INFO";
try {
  bundleManager.getPermissionDef(permissionName).then((data) => {
    hilog.info(0x0000, 'testTag', 'getPermissionDef successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getPermissionDef failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getPermissionDef failed. Cause: %{public}s', message);
}

```

