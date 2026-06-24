# setMultiScreenRelativePosition（系统接口）

## setMultiScreenRelativePosition

```TypeScript
function setMultiScreenRelativePosition(mainScreenOptions: MultiScreenPositionOptions,
    secondaryScreenOptions: MultiScreenPositionOptions): Promise<void>
```

������չģʽ�£�������������չ��Ļ��λ����Ϣ��ʹ��Promise�첽�ص���

**起始版本：** 13

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mainScreenOptions | MultiScreenPositionOptions | 是 | ������λ����Ϣ�� |
| secondaryScreenOptions | MultiScreenPositionOptions | 是 | ��չ��Ļ��λ����Ϣ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �޷��ؽ����Promise���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed, non-system application uses system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. |
| [1400001](../../errorcode-universal.md#1400001-Invalid) | Invalid display or screen. |
| [1400003](../../errorcode-universal.md#1400003-This) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let mainScreenOptions: screen.MultiScreenPositionOptions = {
  id : 0,
  startX : 0,
  startY : 0
};

let secondaryScreenOptions: screen.MultiScreenPositionOptions = {
  id : 12,
  startX : 1000,
  startY : 1000
};

screen.setMultiScreenRelativePosition(mainScreenOptions, secondaryScreenOptions).then(() => {
  console.info('Succeeded in setting multi screen relative position.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set multi screen relative position. Code:${err.code}, message is ${err.message}`);
});

```

