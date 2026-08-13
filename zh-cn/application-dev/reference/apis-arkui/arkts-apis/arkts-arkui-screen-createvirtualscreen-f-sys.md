# createVirtualScreen（系统接口）

## createVirtualScreen

```TypeScript
function createVirtualScreen(options:VirtualScreenOption, callback: AsyncCallback<Screen>): void
```

创建虚拟屏幕，使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.CAPTURE_SCREEN

<!--Device-screen-function createVirtualScreen(options:VirtualScreenOption, callback: AsyncCallback<Screen>): void--><!--Device-screen-function createVirtualScreen(options:VirtualScreenOption, callback: AsyncCallback<Screen>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [VirtualScreenOption](arkts-arkui-screen-virtualscreenoption-i-sys.md) | 是 | 用于创建虚拟屏幕的参数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[Screen](arkts-arkui-screen-screen-i-sys.md)&gt; | 是 | 回调函数，返回创建的虚拟屏幕对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let screenClass: screen.Screen | null = null;
class VirtualScreenOption {
  name : string = '';
  width : number =  0;
  height : number = 0;
  density : number = 0;
  surfaceId : string = '';
  supportsFocus ?: boolean = true;
}

let option: VirtualScreenOption = { 
  name: 'screen01',
  width: 1080,
  height: 2340,
  density: 2,
  surfaceId: '',
  supportsFocus: false
}; // 创建虚拟屏幕的参数
// 创建虚拟屏幕
screen.createVirtualScreen(option, (err: BusinessError, data: screen.Screen) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to create the virtual screen. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  screenClass = data;
  console.info(`Succeeded in creating the virtual screen. Data: ${JSON.stringify(data)}`);
});
```

ArkTS-Sta示例：

```TypeScript
let option : screen.VirtualScreenOption = { 
  name: 'screen01',
  width: 1080,
  height: 2340,
  density: 2,
  surfaceId: ''
};
screen.createVirtualScreen(option, (err: BusinessError | null, data) => {
  const errCode = err?.code;
  if (errCode) {
    console.error(`Failed to create the virtual screen. Code: ${err?.code}, message: ${err?.message}`);
    return;
  }
  console.info(`Succeeded in creating the virtual screen. Data: ${JSON.stringify(data)}`);
});
```


## createVirtualScreen

```TypeScript
function createVirtualScreen(options:VirtualScreenOption): Promise<Screen>
```

创建虚拟屏幕，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.CAPTURE_SCREEN

<!--Device-screen-function createVirtualScreen(options:VirtualScreenOption): Promise<Screen>--><!--Device-screen-function createVirtualScreen(options:VirtualScreenOption): Promise<Screen>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [VirtualScreenOption](arkts-arkui-screen-virtualscreenoption-i-sys.md) | 是 | 用于创建虚拟屏幕的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Screen](arkts-arkui-screen-screen-i-sys.md)&gt; | Promise对象。返回创建的虚拟屏幕对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let screenClass: screen.Screen | null = null;
class VirtualScreenOption {
  name : string = '';
  width : number =  0;
  height : number = 0;
  density : number = 0;
  surfaceId : string = '';
  supportsFocus ?: boolean = true;
}

let option: VirtualScreenOption = { 
  name: 'screen01',
  width: 1080,
  height: 2340,
  density: 2,
  surfaceId: '',
  supportsFocus: false
}; // 创建虚拟屏幕的参数

// 创建虚拟屏幕
screen.createVirtualScreen(option).then((data: screen.Screen) => {
  screenClass = data;
  console.info(`Succeeded in creating the virtual screen. Data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to create the virtual screen. Code: ${err.code}, message: ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
let screenClass: screen.Screen | null = null;

let option : screen.VirtualScreenOption = { 
  name: 'screen01',
  width: 1080,
  height: 2340,
  density: 2,
  surfaceId: ''
};
screen.createVirtualScreen(option).then((data: screen.Screen) => {
  screenClass = data;
  console.info(`Succeeded in creating the virtual screen. Data: ${JSON.stringify(data)}`);
}).catch((err: Error) => {
  console.error(`Failed to create the virtual screen. Code: ${err?.code}, message: ${err?.message}`);
});
```

