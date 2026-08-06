# setVirtualScreenSurface（系统接口）

## setVirtualScreenSurface

```TypeScript
function setVirtualScreenSurface(screenId:long, surfaceId: string, callback: AsyncCallback<void>): void
```

设置虚拟屏幕的surface，使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.CAPTURE_SCREEN

<!--Device-screen-function setVirtualScreenSurface(screenId:long, surfaceId: string, callback: AsyncCallback<void>): void--><!--Device-screen-function setVirtualScreenSurface(screenId:long, surfaceId: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| screenId | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：long | 是 | 屏幕的id，该参数仅支持整数输入。 |
| surfaceId | string | 是 | 代表虚拟屏幕的surface标识符，surfaceId值可自行定义，由用户指定某一实际存在的surface对应的surfaceId。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当设置虚拟屏幕surface成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
// Index.ets
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  xComponentController: XComponentController = new XComponentController();

  setVirtualScreenSurface = () => {
    let screenId: number = 1;// 屏幕ID需通过getAllScreens()获取或从createVirtualScreen()返回值获取
    let surfaceId = this.xComponentController.getXComponentSurfaceId();
    // 设置虚拟屏幕的surface
    screen.setVirtualScreenSurface(screenId, surfaceId, (err: BusinessError) => {
    const errCode: number = err.code;
    if (errCode) {
      console.error(`Failed to set the surface for the virtual screen. Code: ${err.code}, message: ${err.message}`);
      return;
    }
      console.info('Succeeded in setting the surface for the virtual screen.');
    });
  }
  build() {
    RelativeContainer() {
      XComponent({
        type: XComponentType.SURFACE,
        controller: this.xComponentController
      })
      Button('setSurface')
        .onClick((event: ClickEvent) => {
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
screen.setVirtualScreenSurface(screenId, surfaceId, (err: BusinessError | null) => {
  const errCode = err?.code;
  if (errCode) {
    console.error(`Failed to set the surface for the virtual screen. Code: ${err?.code}, message: ${err?.message}`);
    return;
  }
  console.info('Succeeded in setting the surface for the virtual screen.');
});
```


## setVirtualScreenSurface

```TypeScript
function setVirtualScreenSurface(screenId:long, surfaceId: string): Promise<void>
```

设置虚拟屏幕的surface，使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.CAPTURE_SCREEN

<!--Device-screen-function setVirtualScreenSurface(screenId:long, surfaceId: string): Promise<void>--><!--Device-screen-function setVirtualScreenSurface(screenId:long, surfaceId: string): Promise<void>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| screenId | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：long | 是 | 屏幕的id，该参数仅支持整数输入。 |
| surfaceId | string | 是 | 代表虚拟屏幕的surface标识符，surfaceId值可自行定义，由用户指定某一实际存在的surface对应的surfaceId。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
// Index.ets
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  xComponentController: XComponentController = new XComponentController();

  setVirtualScreenSurface = () => {
    let screenId: number = 1;// 屏幕ID需通过getAllScreens()获取或从createVirtualScreen()返回值获取
    let surfaceId = this.xComponentController.getXComponentSurfaceId();
    // 设置虚拟屏幕的surface
    screen.setVirtualScreenSurface(screenId, surfaceId).then(() => {
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
        .onClick((event: ClickEvent) => {
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
screen.setVirtualScreenSurface(screenId, surfaceId).then(() => {
  console.info('Succeeded in setting the surface for the virtual screen.');
}).catch((err: Error) => {
  console.error(`Failed to set the surface for the virtual screen. Code: ${err?.code}, message: ${err?.message}`);
});
```

