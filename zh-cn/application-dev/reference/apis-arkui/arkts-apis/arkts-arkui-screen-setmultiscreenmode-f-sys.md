# setMultiScreenMode（系统接口）

## setMultiScreenMode

```TypeScript
function setMultiScreenMode(primaryScreenId: number, secondaryScreenId: number,
    secondaryScreenMode: MultiScreenMode): Promise<void>
```

������չ��Ļ����ʾģʽ������/��չ����ʹ��Promise�첽�ص���primaryScreenId��secondaryScreenId��Ϊ0ʱ��������չ����ʾ��

**起始版本：** 13

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| primaryScreenId | number | 是 | ������id���ò���ӦΪ�Ǹ������������������ְ���С�����֣�����ȡ���� |
| secondaryScreenId | number | 是 | ��չ��Ļ��id���ò���ӦΪ�Ǹ������������������ְ���С�����֣�����ȡ���� |
| secondaryScreenMode | MultiScreenMode | 是 | ��չ��Ļ����ʾģʽ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �޷��ؽ����Promise���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed, non-system application uses system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. |
| [1400003](../../errorcode-universal.md#1400003-This) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let primaryScreenId: number = 0;
let secondaryScreenId: number = 12;
let screenMode: screen.MultiScreenMode = screen.MultiScreenMode.SCREEN_MIRROR;
screen.setMultiScreenMode(primaryScreenId, secondaryScreenId, screenMode).then(() => {
  console.info('Succeeded in setting multi screen mode. Data: ');
}).catch((err: BusinessError) => {
  console.error(`Failed to set multi screen mode. Code:${err.code}, message is ${err.message}`);
});

```

