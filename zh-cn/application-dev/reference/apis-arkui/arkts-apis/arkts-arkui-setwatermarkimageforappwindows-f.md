# setWatermarkImageForAppWindows

## setWatermarkImageForAppWindows

```TypeScript
function setWatermarkImageForAppWindows(pixelMap: image.PixelMap | undefined): Promise<void>
```

设置或取消本应用进程下窗口的水印图片，使用Promise异步回调。该接口需要在
[loadContent()](arkts-arkui-window-i.md#loadcontent-1)
或[setUIContent()](arkts-arkui-window-i.md#setuicontent-1)调用生效后使
用。

**起始版本：** 21

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pixelMap | image.PixelMap \| undefined | 是 | 传入`image.PixelMap`表示设置水印图片，传入`undefined`表示取消水印显示。<br/>如果图片尺寸的宽和高同时超过窗口尺寸以及屏幕尺寸的宽和高，返回错误码1300016。<br/>如果图片尺寸的宽或高超过窗口尺寸的宽或高，超出窗口宽或高的部分会被裁剪。<br/>如果图片尺寸的宽或高小于窗口尺寸的宽或高，小于的部分会自动重复补充。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Function setWatermarkImageForAppWindows can not to work correctly due to limited device capabilities. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300016](../errorcode-window.md#1300016-参数校验错误) | Parameter error. Possible cause: 1. Invalid parameter range. |

**示例：**

```TypeScript
import { image } from "@kit.ImageKit";
import { BusinessError } from "@kit.BasicServicesKit";

let color: ArrayBuffer = new ArrayBuffer(96);
let initializationOptions: image.InitializationOptions = {
  editable: true,
  pixelFormat: image.PixelMapFormat.RGBA_8888,
  size: {
    height: 4,
    width: 6,
  },
};
image.createPixelMap(color, initializationOptions).then((pixelMap: image.PixelMap) => {
  console.info("Succeeded in creating pixelmap.");
  try {
    let promise = window.setWatermarkImageForAppWindows(pixelMap);
    promise.then(() => {
        console.info("Succeeded in setting watermark image.");
    }).catch((err: BusinessError) => {
      console.error(`Failed to set watermark image. Cause code: ${err.code}, message: ${err.message}`);
    });
  } catch (exception) {
    console.error(`Failed to set watermark image. Exception code: ${exception.code}, message: ${exception.message}`);
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to create PixelMap. Cause code: ${err.code}, message: ${err.message}`);
});

```

