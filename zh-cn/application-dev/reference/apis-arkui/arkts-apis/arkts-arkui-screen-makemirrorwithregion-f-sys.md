# makeMirrorWithRegion（系统接口）

## makeMirrorWithRegion

```TypeScript
function makeMirrorWithRegion(mainScreen: number, mirrorScreen: Array<number>, mainScreenRegion: Rect): Promise<number>
```

����Ļ��ĳһ������������Ϊ����ģʽ��ʹ��Promise�첽�ص������øýӿں󣬲������ٽ�����Ļ����ת/�۵���������ܵ��¾��������쳣��

**起始版本：** 19

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mainScreen | number | 是 | ����ĻID���ò�����֧�����������롣 |
| mirrorScreen | Array&lt;number&gt; | 是 | ������ĻID���ϡ�����IDӦΪ�������� |
| mainScreenRegion | Rect | 是 | ������������ľ������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise���󡣷��ؾ�����Ļ��Ⱥ��id������idΪ�������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [1400001](../../errorcode-universal.md#1400001-Invalid) | Invalid display or screen. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let mainScreenId: number = 0;
let mirrorScreenIds: Array<number> = [1, 2, 3];
let mainScreenRegion: screen.Rect = {
  left : 0,
  top : 0,
  width : 1920,
  height : 1080
};
screen.makeMirrorWithRegion(mainScreenId, mirrorScreenIds, mainScreenRegion).then((data: number) => {
  console.info(`Succeeded in setting screen mirroring. Data: ${data}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set screen area mirroring. Code:${err.code}, message is ${err.message}`);
});

```

