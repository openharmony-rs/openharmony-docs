# dumpJsHeapData

## dumpJsHeapData

```TypeScript
function dumpJsHeapData(filename : string) : void
```

�����������ת����

> **ע��**
>
> ����������ѵ��������ʱ���Ҹýӿ�Ϊͬ���ӿڣ����鲻Ҫ���ϼܰ汾�е��øýӿڣ��Ա���Ӧ�ö�����Ӱ���û����顣

**起始版本：** 9

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filename | string | 是 | �û��Զ���������������ת��������ļ���������Ӧ�õ�`files`Ŀ¼�������Ըò���������heapsnapshot�ļ���string���ȵ����ֵΪ128�ֽڡ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | the parameter check failed, Parameter type error |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  hidebug.dumpJsHeapData("heapData");
} catch (error) {
  console.error(`error code: ${(error as BusinessError).code}, error msg: ${(error as BusinessError).message}`);
}

```


## dumpJsHeapData

```TypeScript
function dumpJsHeapData(filename: string, needClean: boolean): void
```

�����������ת����֧�����nodeId���档

> **ע��**
>
> ����������ѵ��������ʱ���Ҹýӿ�Ϊͬ���ӿڣ����鲻Ҫ���ϼܰ汾�е��øýӿڣ��Ա���Ӧ�ö�����Ӱ���û����顣

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本24开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filename | string | 是 | �û��Զ�����������ת���ļ���������Ӧ�õ�filesĿ¼������fileName.heapsnapshot��ʽ�ļ���string���ȵ����ֵΪ128�ֽڡ� |
| needClean | boolean | 是 | ת���ѿ���ǰ�Ƿ���Ҫ���nodeId���档true����Ҫ�����false������Ҫ����� |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  hidebug.dumpJsHeapData("heapData", true);
} catch (error) {
  console.error(`error code: ${(error as BusinessError).code}, error msg: ${(error as BusinessError).message}`);
}

```

