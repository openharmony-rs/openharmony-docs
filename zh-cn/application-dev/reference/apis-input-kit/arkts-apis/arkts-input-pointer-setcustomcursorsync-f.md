# setCustomCursorSync

## 导入模块

```TypeScript
import { pointer } from '@kit.InputKit';
```

## setCustomCursorSync

```TypeScript
function setCustomCursorSync(windowId: int, pixelMap: image.PixelMap, focusX?: int, focusY?: int): void
```

设置指定窗口的自定义光标样式，使用同步方式进行设置。此接口仅支持设置本应用进程内窗口的自定义光标样式，如需通过UIExtensionAbility进程设置宿主窗口的自定义光标样式，请参阅 [setCustomCursor](../../../reference/apis-arkui/arkts-apis-uicontext-cursorcontroller.md#setcustomcursor)。<br>应用窗口布局改变、热区切换、页面跳转、光标移出再回到窗口、光标在窗口不同区域移动， 以上场景可能导致光标切换回系统样式，需要开发者重新设置光标样式。

**起始版本：** 23

<!--Device-pointer-function setCustomCursorSync(windowId: int, pixelMap: image.PixelMap, focusX?: int, focusY?: int): void--><!--Device-pointer-function setCustomCursorSync(windowId: int, pixelMap: image.PixelMap, focusX?: int, focusY?: int): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowId | int | 是 | 窗口ID。取值为大于0的整数。 |
| pixelMap | image.PixelMap | 是 | 自定义光标资源。 |
| focusX | int | 否 | 自定义光标焦点x，取值范围：大于等于0，默认为0，单位为像素（px）。 |
| focusY | int | 否 | 自定义光标焦点y，取值范围：大于等于0，默认为0，单位为像素（px）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

ArkTS-Dyn示例:

```TypeScript
import { pointer } from '@kit.InputKit';
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // app_icon为示例资源，请开发者根据实际需求配置资源文件。
          this.getUIContext()?.getHostContext()?.resourceManager.getMediaContent(
            $r('app.media.app_icon').id, (error: BusinessError, svgFileData: Uint8Array) => {
            const svgBuffer = svgFileData.buffer;
            let svgImageSource: image.ImageSource = image.createImageSource(svgBuffer);
            // 光标图片宽高
            let svgDecodingOptions: image.DecodingOptions = { desiredSize: { width: 50, height: 50 } };
            // 创建PixelMap
            svgImageSource.createPixelMap(svgDecodingOptions).then((pixelMap) => {
              // 获取应用内最近一个窗口
              window.getLastWindow(this.getUIContext().getHostContext(), (error: BusinessError, win: window.Window) => {
                let windowId = win.getWindowProperties().id;
                try {
                  // 同步设置自定义光标
                  pointer.setCustomCursorSync(windowId, pixelMap, 25, 25);
                  console.info(`Succeeded in setting custom cursor sync.`);
                } catch (error) {
                  console.error(`Failed to set custom cursor sync, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                }
              });
            }).catch((error: BusinessError) => {
              console.error(`Failed to create pixel map promise, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            });
          });
        }
      )
    }
  }
}
```

ArkTS-Sta示例:

```TypeScript
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { pointer } from '@kit.InputKit';
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let width: int = 64;
          let height: int = 64;
          const buffer = new ArrayBuffer(width * height * 4); // RGBA_8888
          const pixelView = new Uint8Array(buffer);
          for (let i = 0; i < pixelView.length; i += 4) {
            pixelView[i] = 0xFF;  // Set the RGBA channel values
            pixelView[i+1] = 0x00;
            pixelView[i+2] = 0x00;
            pixelView[i+3] = 0xFF; // opaque
          }
          const opts: image.InitializationOptions = {
            editable: true,
            pixelFormat: image.PixelMapFormat.RGBA_8888,
            size: { width: width, height: height }
          };
          let img = image.createPixelMapSync(buffer, opts);
          // 此次根据实际获取窗口id
          let windowId: int = 100;
          try {
            // 同步设置自定义光标
            pointer.setCustomCursorSync(windowId, img, 25, 25);
          } catch (error) {
            console.error(`Failed to set custom cursor sync, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

