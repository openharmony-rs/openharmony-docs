# setVirtualScreenSurface

## setVirtualScreenSurface

```TypeScript
function setVirtualScreenSurface(screenId: long, surfaceId: string): Promise<void>
```

设置虚拟屏幕的surfaceId。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.ACCESS_VIRTUAL_SCREEN

<!--Device-display-function setVirtualScreenSurface(screenId: long, surfaceId: string): Promise<void>--><!--Device-display-function setVirtualScreenSurface(screenId: long, surfaceId: string): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| screenId | long | 是 | 屏幕ID，与创建的虚拟屏幕ID保持一致，即使用[createVirtualScreen()](arkts-arkui-display-createvirtualscreen-f.md#createVirtualScreen)接口成功创建对 应虚拟屏幕时的返回值，该参数仅支持整数输入。 |
| surfaceId | string | 是 | 代表虚拟屏幕绑定的surfaceId，由用户指定某一实际存在的surface对应的surfaceId，该参数最大长度为4096个字节，超出最大长度时则取前4096个字节。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |

## 示例

ArkTS-Dyn示例：

```TypeScript
// Index.ets
import { display } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  xComponentController: XComponentController = new XComponentController();

  setVirtualScreenSurface = () => {
    let screenId: number = 1;
    let surfaceId = this.xComponentController.getXComponentSurfaceId();
    display.setVirtualScreenSurface(screenId, surfaceId).then(() => {
      console.info('Succeeded in setting the surface for the virtual screen.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to set the surface for the virtual screen. Code: ${err.code}, message: ${err.message}`);
    });
  }
  build() {
    RelativeContainer() {
      XComponent({
        type: XComponentType.SURFACE,
        controller: this.xComponentController
      })
      Button('setSurface')
        .onClick(() => {
          this.setVirtualScreenSurface();
      }).width('100%')
      .height(20)
    }
    .width('100%')
    .height('100%')
  }
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let screenId: long = 1;
let surfaceId: string = '2048';
display.setVirtualScreenSurface(screenId, surfaceId).then(() => {
  console.info('Succeeded in setting the surface for the virtual screen.');
}).catch((err: Error) => {
  console.error(`Failed to set the surface for the virtual screen. Code: ${err?.code}, message: ${err?.message}`);
});
```

