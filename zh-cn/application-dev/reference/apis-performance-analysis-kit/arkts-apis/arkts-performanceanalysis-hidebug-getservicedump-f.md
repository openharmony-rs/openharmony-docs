# getServiceDump

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

<a id="getservicedump"></a>
## getServiceDump

```TypeScript
function getServiceDump(serviceid : number, fd : number, args : Array<string>) : void
```

��ȡϵͳ������Ϣ��

**起始版本：** 9

**需要权限：** ohos.permission.DUMP

<!--Device-hidebug-function getServiceDump(serviceid : int, fd : int, args : Array<string>) : void--><!--Device-hidebug-function getServiceDump(serviceid : int, fd : int, args : Array<string>) : void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| serviceid | number | 是 | ϵͳ����ID�����ڱ�ʶҪ��ȡ��Ϣ��ϵͳ����ȡֵ��ϵͳ���壬ȡֵ��Χ[0, 255]��������Чֵʱ���ش�����401�� |
| fd | number | 是 | �ļ����������ӿڻ����fdд�����ݡ�������Ч�ļ�������ʱ���ش�����401�� |
| args | Array&lt;string&gt; | 是 | ϵͳ�����dump�ӿڲ����б���string���ȵ����ֵΪ254���������ֽ��ᱻ�ضϡ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | the parameter check failed, Possible causes:1.the parameter type error2.the args parameter is not string array |
| [11400101](../errorcode-hiviewdfx-hidebug.md#11400101-系统服务获取失败) | ServiceId invalid. The system ability does not exist. |

**示例：**

```TypeScript
import { fileIo } from '@kit.CoreFileKit';
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

let fileFd = -1;
try {
  // 请在组件内获取context，确保this.getUiContext().getHostContext()返回结果为UIAbilityContext。
  let path: string = this.getUIContext().getHostContext()!.filesDir + "/serviceInfo.txt";
  console.info("output path: " + path);
  fileFd = fileIo.openSync(path, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE).fd;
  let serviceId: number = 10;
  let args: Array<string> = new Array("allInfo");
  hidebug.getServiceDump(serviceId, fileFd, args);
} catch (error) {
  console.error(`error code: ${(error as BusinessError).code}, error msg: ${(error as BusinessError).message}`);
}

if (fileFd >= 0) {
  fileIo.closeSync(fileFd);
}

```

