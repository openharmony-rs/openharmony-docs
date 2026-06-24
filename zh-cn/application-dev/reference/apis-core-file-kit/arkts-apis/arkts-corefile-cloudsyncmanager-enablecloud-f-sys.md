# enableCloud（系统接口）

## enableCloud

```TypeScript
function enableCloud(accountId: string, switches: Record<string, boolean>): Promise<void>
```

�첽����ʹ�ܶ���Эͬ������ʹ��Promise�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | �˺�Id�� |
| switches | Record&lt;string, boolean&gt; | 是 | Ӧ�õĶ���Эͬ����ʹ�ܿ��أ�string����ΪӦ�ð�����boolean����Ϊ����״̬��trueΪ�򿪣�falseΪ�رա� |

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
let switches: Record<string, boolean> = {
  'com.example.bundleName1': true,
  'com.example.bundleName2': false
}
cloudSyncManager.enableCloud(accountId, switches).then(() => {
  console.info("enableCloud successfully.");
}).catch((err: BusinessError) => {
  console.error("enableCloud failed with error message: " + err.message + ", error code: " + err.code);
});

```


## enableCloud

```TypeScript
function enableCloud(
    accountId: string,
    switches: Record<string, boolean>,
    callback: AsyncCallback<void>
  ): void
```

�첽����ʹ�ܶ���Эͬ������ʹ��callback�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | �˺�Id�� |
| switches | Record&lt;string, boolean&gt; | 是 | Ӧ�õĶ���Эͬ����ʹ�ܿ��أ�string����ΪӦ�ð�����boolean����Ϊ����״̬��trueΪ�򿪣�falseΪ�رա� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص��������첽ʹ�ܶ���Эͬ����֮�� |

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
let switches: Record<string, boolean> = {
  'com.example.bundleName1': true,
  'com.example.bundleName2': false
}
cloudSyncManager.enableCloud(accountId, switches, (err: BusinessError) => {
  if (err) {
    console.error("enableCloud failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("enableCloud successfully");
  }
});

```

