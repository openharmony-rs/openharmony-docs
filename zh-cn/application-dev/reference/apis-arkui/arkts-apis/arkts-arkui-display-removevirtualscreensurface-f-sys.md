# removeVirtualScreenSurface（系统接口）

## 导入模块

```TypeScript
import { display } from '@kit.ArkUI';
```

<a id="removevirtualscreensurface"></a>
## removeVirtualScreenSurface

```TypeScript
function removeVirtualScreenSurface(screenId: number, surfaceId: string): Promise<void>
```

删除虚拟屏的surface。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-display-function removeVirtualScreenSurface(screenId: long, surfaceId: string): Promise<void>--><!--Device-display-function removeVirtualScreenSurface(screenId: long, surfaceId: string): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| screenId | number | 是 | 虚拟屏幕的屏幕ID。 |
| surfaceId | string | 是 | 代表虚拟屏幕绑定的surfaceId，由用户指定某一实际存在的surface对应的surfaceId，该参数最大长度为4096个字节，超出最大长度时则取前4096个字节。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function removeVirtualScreenSurface can not work correctly due to limited device capabilities. |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |
| [1400004](../errorcode-display.md#1400004-参数异常) | Parameter error. Possible cause: 1. Invalid parameter range. |

**示例：**

```TypeScript
// Index.ets
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  xComponentController: XComponentController = new XComponentController();

  removeVirtualScreenSurface = () => {
    let screenId: number = 1;
    let surfaceId = this.xComponentController.getXComponentSurfaceId();
    display.removeVirtualScreenSurface(screenId, surfaceId).then(() => {
      console.info('Succeeded in removing surface for the virtual screen.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to remove surface for the virtual screen. Code:${err.code}, message is ${err.message}`);
    });
  }
  build() {
    RelativeContainer() {
      XComponent({
        type: XComponentType.SURFACE,
        controller: this.xComponentController
      })
      Button('removeSurface')
        .onClick((event: ClickEvent) => {
          this.removeVirtualScreenSurface();
      }).width('100%')
      .height(20)
    }
    .width('100%')
    .height('100%')
  }
}

```

