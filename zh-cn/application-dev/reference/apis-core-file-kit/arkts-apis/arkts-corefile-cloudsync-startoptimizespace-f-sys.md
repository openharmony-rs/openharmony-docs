# startOptimizeSpace（系统接口）

## startOptimizeSpace

```TypeScript
function startOptimizeSpace(optimizePara: OptimizeSpaceParam, callback?: Callback<OptimizeSpaceProgress>): Promise<void>
```

�Ż�ͼ����ͬ���ƿռ�ı�����Դ��ִ�������Ż��ռ���ԣ����ϻ�����ǰδ���ʵı���ͼƬ/��Ƶ�����Ż���ʹ��Promise�첽�ص���callback�����Ż����ȡ�

startOptimizeSpace��ʹ�ú�stopOptimizeSpace��������һһ��Ӧ���ظ�����������������������ִ�еĴ�����Ϣ��22400006����

**起始版本：** 17

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| optimizePara | OptimizeSpaceParam | 是 | �Ż������� |
| callback | Callback&lt;OptimizeSpaceProgress&gt; | 否 | �ص������������Ż����ȣ�ȱʡ����·���401���󣬲�ִ���������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed, application which is not a system application uses<br/>system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2<br/>.Incorrect parameter types. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. |
| [22400005](../../errorcode-universal.md#22400005-Inner) | Inner error. |
| [22400006](../../errorcode-universal.md#22400006-The) | The same task is already in progress. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let para:cloudSync.OptimizeSpaceParam = {totalSize: 1073741824, agingDays: 30};
let callback = (data:cloudSync.OptimizeSpaceProgress) => {
  if (data.state == cloudSync.OptimizeState.FAILED) {
    console.info("optimize space failed");
  } else if (data.state == cloudSync.OptimizeState.COMPLETED && data.progress == 100) {
    console.info("optimize space successfully");
  } else if (data.state == cloudSync.OptimizeState.RUNNING) {
    console.info("optimize space progress: " + data.progress);
  }
}
cloudSync.startOptimizeSpace(para, callback).then(() => {
  console.info("start optimize space");
}).catch((err: BusinessError) => {
  console.error("start optimize space failed with error message: " + err.message + ", error code: " + err.code);
});

```

