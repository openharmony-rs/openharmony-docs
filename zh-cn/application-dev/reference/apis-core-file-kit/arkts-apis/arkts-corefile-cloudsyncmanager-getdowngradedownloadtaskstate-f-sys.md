# getDowngradeDownloadTaskState（系统接口）

## getDowngradeDownloadTaskState

```TypeScript
function getDowngradeDownloadTaskState(bundleNames: Array<string>): Promise<Array<DownloadProgress>>
```

��ѯ�������̵�Ӧ�õ�ȫ����������״̬��ʹ��Promise�첽�ص���

���ڷ��ص�DownloadProgress�����в�����������Ϣ�������������ѯ���Ӧ��ʱ�����÷������м�¼Ӧ�ð�����

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CLOUDFILE_SYNC_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleNames | Array&lt;string&gt; | 是 | ��Ҫ��ѯ��Ӧ�ð������飬ÿ��Ԫ��ΪӦ�õİ����ַ��������������С����Ϊ20���� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;DownloadProgress&gt;&gt; | - Promise���󣬷��ز�ѯ��ȫ�����������״̬��Ϣ���顣 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [13900010](../../errorcode-universal.md#13900010-Try) | Try again. |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument. Possible causes:<br/><br/>1.Mandatory parameter are left unspecified. 2.The length of the input parameter exceeds the upper limit.<br/><br/>3.The input parameter contains an invalid bundleName. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let bundles: Array<string> = ['com.example.app1', 'com.example.app2'];
cloudSyncManager.getDowngradeDownloadTaskState(bundles).then((results: Array<cloudSyncManager.DownloadProgress>) => {
  results.forEach((item) => {
    console.info(`state: ${item.state}, downloadedSize: ${item.downloadedSize}, totalSize: ${item.totalSize}`);
    console.info(`successfulCount: ${item.successfulCount}, failedCount: ${item.failedCount}, totalCount: ${item.totalCount}`);
    if (item.state == cloudSyncManager.DownloadState.STOPPED) {
      console.info(`stopReason: ${item.stopReason}`);
    }
  });
}).catch((err: BusinessError) => {
  console.error(`getDowngradeDownloadTaskState failed, code: ${err.code}, message: ${err.message}`);
});

```

