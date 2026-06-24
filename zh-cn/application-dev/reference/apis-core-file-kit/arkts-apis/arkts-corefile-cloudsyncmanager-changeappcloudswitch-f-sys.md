# changeAppCloudSwitch（系统接口）

## changeAppCloudSwitch

```TypeScript
function changeAppCloudSwitch(accountId: string, bundleName: string, status: boolean): Promise<void>
```

�첽�����޸�Ӧ�õĶ����ļ�ͬ�����ء�ʹ��Promise�첽�ص���

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | �˺�Id�� |
| bundleName | string | 是 | Ӧ�ð����� |
| status | boolean | 是 | �޸ĵ�Ӧ����ͬ������״̬��trueΪ�򿪣�falseΪ�رա� |

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
let bundleName: string = "com.example.bundle";
cloudSyncManager.changeAppCloudSwitch(accountId, bundleName, true).then(() => {
  console.info("changeAppCloudSwitch successfully");
}).catch((err: BusinessError) => {
  console.error("changeAppCloudSwitch failed with error message: " + err.message + ", error code: " + err.code);
});

```


## changeAppCloudSwitch

```TypeScript
function changeAppCloudSwitch(accountId: string, bundleName: string, status: boolean, callback: AsyncCallback<void>): void
```

�첽�����޸�Ӧ�õĶ����ļ�ͬ�����ء�ʹ��callback�첽�ص���

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | �˺�Id�� |
| bundleName | string | 是 | Ӧ�ð��� |
| status | boolean | 是 | �޸ĵ�Ӧ����ͬ������״̬��trueΪ�򿪣�falseΪ�رա� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص��������첽�޸�Ӧ�õĶ����ļ�ͬ������֮�� |

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
let bundleName: string = "com.example.bundle";
cloudSyncManager.changeAppCloudSwitch(accountId, bundleName, true, (err: BusinessError) => {
  if (err) {
    console.error("changeAppCloudSwitch failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("changeAppCloudSwitch successfully");
  }
});

```

