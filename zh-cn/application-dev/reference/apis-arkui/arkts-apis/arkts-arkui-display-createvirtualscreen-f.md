# createVirtualScreen

## 导入模块

```TypeScript
import { display } from '@kit.ArkUI';
```

## createVirtualScreen

```TypeScript
function createVirtualScreen(config: VirtualScreenConfig): Promise<number>
```

创建虚拟屏幕，使用Promise异步回调。

**起始版本：** 16

**需要权限：** ohos.permission.ACCESS_VIRTUAL_SCREEN

<!--Device-display-function createVirtualScreen(config: VirtualScreenConfig): Promise<long>--><!--Device-display-function createVirtualScreen(config: VirtualScreenConfig): Promise<long>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [VirtualScreenConfig](arkts-arkui-display-virtualscreenconfig-i.md) | 是 | 用于创建虚拟屏幕的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象。返回创建的虚拟屏幕的ScreenId。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function createVirtualScreen can not work correctly due to limited device capabilities. |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

class VirtualScreenConfig {
  name : string = '';
  width : number = 0;
  height : number = 0;
  density : number = 0;
  surfaceId : string = '';
  supportsFocus ?: boolean = true;
}

let config: VirtualScreenConfig = {
  name: 'screen01',
  width: 1080,
  height: 2340,
  density: 2,
  surfaceId: '',
  supportsFocus: false
};

display.createVirtualScreen(config).then((screenId: number) => {
  console.info(`Succeeded in creating the virtual screen. ScreenId: ${screenId}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to create the virtual screen. Code: ${err.code}, message: ${err.message}`);
});

```

