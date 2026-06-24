# clean（系统接口）

## clean

```TypeScript
function clean(accountId: string, appActions: Record<string, Action>): Promise<void>
```

�첽��������������������ݡ�ʹ��Promise�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | �˺�Id�� |
| appActions | Record&lt;string, Action&gt; | 是 | �����������ͣ�string����Ϊ������Ӧ�ð����� [Action](arkts-corefile-cloudsyncmanager-action-e-sys.md#Action)Ϊ������<br/>�����͡� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;<br/><br/>2.Incorrect parameter types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
let appActions: Record<string, cloudSyncManager.Action> = {
  'com.example.bundleName1': cloudSyncManager.Action.RETAIN_DATA,
  'com.example.bundleName2': cloudSyncManager.Action.CLEAR_DATA
};
cloudSyncManager.clean(accountId, appActions).then(() => {
  console.info("clean successfully");
}).catch((err: BusinessError) => {
  console.error("clean failed with error message: " + err.message + ", error code: " + err.code);
});

```


## clean

```TypeScript
function clean(accountId: string, appActions: Record<string, Action>, callback: AsyncCallback<void>): void
```

�첽��������������������ݡ�ʹ��callback�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | �˺�Id�� |
| appActions | Record&lt;string, Action&gt; | 是 | �����������ͣ�string����Ϊ������Ӧ�ð����� [Action](arkts-corefile-cloudsyncmanager-action-e-sys.md#Action)Ϊ������<br/>�����͡� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص��������첽��������������������ݡ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;<br/><br/>2.Incorrect parameter types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
  let appActions: Record<string, cloudSyncManager.Action> = {
  'com.example.bundleName1': cloudSyncManager.Action.RETAIN_DATA,
  'com.example.bundleName2': cloudSyncManager.Action.CLEAR_DATA
};
cloudSyncManager.clean(accountId, appActions, (err: BusinessError) => {
  if (err) {
    console.error("clean failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("clean successfully");
  }
});

```

