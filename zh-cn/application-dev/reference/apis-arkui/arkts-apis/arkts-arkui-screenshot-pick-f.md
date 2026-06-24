# pick

## pick

```TypeScript
function pick(): Promise<PickInfo>
```

��ȡ��Ļ��ͼ����ǰ��֧�ֻ�ȡdisplayIdΪ0����Ļ��ͼ�������Ҫ����չ����ͼ������ͨ��[capture](arkts-arkui-screenshot-capture-f.md#capture-1)�ӿ�ʵ�֣���ʹ��Promise�첽�ص���

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PickInfo&gt; | Promise���󡣷���һ��PickInfo���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported on this device. |
| [1400003](../../errorcode-universal.md#1400003-This) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let promise = screenshot.pick();
  promise.then((pickInfo: screenshot.PickInfo) => {
    console.info('pick Pixel bytes number: ' + pickInfo.pixelMap.getPixelBytesNumber());
    console.info('pick Rect: ' + pickInfo.pickRect);
    pickInfo.pixelMap.release(); // PixelMap使用完后及时释放内存
  }).catch((err: BusinessError) => {
    console.error(`Failed to pick. Code: ' + Code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to pick Code: ' + Code: ${exception.code}, message: ${exception.message}`);
};

```

