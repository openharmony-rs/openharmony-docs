# pick

## pick

```TypeScript
function pick(): Promise<PickInfo>
```

获取屏幕截图，当前仅支持获取displayId为0的屏幕截图（如果需要对扩展屏截图，可以通过[capture](arkts-arkui-capture-f.md#capture-1)接口实现），使用Promise异步回调。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PickInfo&gt; | Promise对象。返回一个PickInfo对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported on this device. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 调用pick接口获取屏幕截图
  let promise = screenshot.pick();
  promise.then((pickInfo: screenshot.PickInfo) => {
    console.info(`pick Pixel bytes number: ${pickInfo.pixelMap.getPixelBytesNumber()}`);
    console.info(`pick Rect: ${pickInfo.pickRect}`);
    pickInfo.pixelMap.release(); // PixelMap使用完后及时释放内存
  }).catch((err: BusinessError) => {
    console.error(`Failed to pick. Code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to pick. Code: ${exception.code}, message: ${exception.message}`);
}

```

