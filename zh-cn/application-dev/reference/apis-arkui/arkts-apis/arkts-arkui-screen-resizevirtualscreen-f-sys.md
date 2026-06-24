# resizeVirtualScreen（系统接口）

## resizeVirtualScreen

```TypeScript
function resizeVirtualScreen(screenId:number, width: number, height: number): Promise<void>
```

�޸�ָ���������ĳߴ磬ʹ��Promise�첽�ص���

**起始版本：** 24

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| screenId | number | 是 | Ҫ�޸ĵ�����������ĻID��ȡֵ��ΧΪ[1000, 2147483647]����������������Ч��Χʱ���ش�����1400004�� |
| width | number | 是 | ���������¿��ȣ���λΪpx��ȡֵ��ΧΪ[1, 65536]����������������Ч��Χʱ���ش�����1400004�� |
| height | number | 是 | ���������¸߶ȣ���λΪpx��ȡֵ��ΧΪ[1, 65536]����������������Ч��Χʱ���ش�����1400004�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. Function can not work because the current device does<br/>not support this ability. |
| [1400001](../../errorcode-universal.md#1400001-Invalid) | Invalid display or screen. |
| [1400003](../../errorcode-universal.md#1400003-This) | This display manager service works abnormally. |
| [1400004](../../errorcode-universal.md#1400004-Parameter) | Parameter error. Possible cause: 1. Invalid parameter range. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let screenId: number = 1000;
let width: number = 1920;
let height: number = 1080;
screen.resizeVirtualScreen(screenId, width, height).then(() => {
  console.info(`Succeeded in resizing virtual screen: screenId=${screenId}, width=${width}, height=${height}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set screen area mirroring. Code:${err.code}, message is ${err.message}`);
});

```

