# canOpenLink

## canOpenLink

```TypeScript
function canOpenLink(link: string): boolean
```

���ݸ����������ж�Ŀ��Ӧ���Ƿ�ɷ��ʣ������е�scheme��Ҫ��[module.json5�ļ�](../../../../quick-start/module-configuration-file.md)��querySchemes�ֶ�
�����á�

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| link | string | 是 | ��ʾ��Ҫ��ѯ�����ӡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | ����true��ʾ���������ӿ��Դ򿪣�����false��ʾ���������Ӳ��ܴ򿪡� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700055](../../errorcode-universal.md#17700055-The) | The specified link is invalid. |
| [17700056](../../errorcode-universal.md#17700056-The) | The scheme of the specified link is not in the querySchemes. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let link = 'welink://';
  let data = bundleManager.canOpenLink(link);
  hilog.info(0x0000, 'testTag', 'canOpenLink successfully: %{public}s', JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'canOpenLink failed: %{public}s', message);
}

```

