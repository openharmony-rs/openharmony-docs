# Screen（系统接口）

[物理屏](../../../../displaymanager/display-terminology.md#物理屏)屏幕实例。

下列API示例中都需先使用[getAllScreens()](arkts-arkui-screen-getallscreens-f-sys.md#getallscreens-1)、[createVirtualScreen()](arkts-arkui-screen-createvirtualscreen-f-sys.md#createvirtualscreen-1)中的任一方法获取到Screen实例，再通过此实例调用对应方法。

**起始版本：** 9

<!--Device-screen-interface Screen--><!--Device-screen-interface Screen-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { screen } from '@kit.ArkUI';
```

## setDensityDpi

```TypeScript
setDensityDpi(densityDpi: number, callback: AsyncCallback<void>): void
```

设置屏幕的像素密度，使用callback异步回调。

**起始版本：** 9

<!--Device-Screen-setDensityDpi(densityDpi: double, callback: AsyncCallback<void>): void--><!--Device-Screen-setDensityDpi(densityDpi: double, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| densityDpi | number | 是 | 像素密度。支持的输入范围为[80, 640]，该参数仅支持整数输入。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当设置屏幕的像素密度成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let densityDpi: number = 320;
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
};

// 创建虚拟屏幕
screen.createVirtualScreen(option).then((data: screen.Screen) => {
  let screenClass: screen.Screen = data;
  console.info(`Succeeded in creating the virtual screen. Data: ${JSON.stringify(data)}`);
  // 设置屏幕的像素密度
  screenClass.setDensityDpi(densityDpi, (err: BusinessError) => {
    const errCode: number = err.code;
    if (errCode) {
      console.error(`Failed to set the pixel density of the screen to 320. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in setting the density dpi.');
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to create the virtual screen. Code: ${err.code}, message: ${err.message}`);
});

```

## setDensityDpi

```TypeScript
setDensityDpi(densityDpi: number): Promise<void>
```

设置屏幕的像素密度，使用Promise异步回调。

**起始版本：** 9

<!--Device-Screen-setDensityDpi(densityDpi: double): Promise<void>--><!--Device-Screen-setDensityDpi(densityDpi: double): Promise<void>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| densityDpi | number | 是 | 像素密度。支持的输入范围为[80, 640]，该参数仅支持整数输入。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let densityDpi: number = 320;
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
};

// 创建虚拟屏幕
screen.createVirtualScreen(option).then((data: screen.Screen) => {
  let screenClass: screen.Screen = data;
  // 设置屏幕的像素密度
  let promise: Promise<void> = screenClass.setDensityDpi(densityDpi);
  promise.then(() => {
    console.info('Succeeded in setting the pixel density of the screen to 320.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set the pixel density of the screen to 320. Code: ${err.code}, message: ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to create the virtual screen. Code: ${err.code}, message: ${err.message}`);
});

```

## setOrientation

```TypeScript
setOrientation(orientation: Orientation, callback: AsyncCallback<void>): void
```

设置屏幕方向，使用callback异步回调。当设置的方向符合[应用旋转策略](../../../../quick-start/module-configuration-file.md#abilities标签)（可通过配置module.json5文件中abilities标签的orientation字段设置应用旋转策略）时，屏幕方向才会发生改变；当设置方向不符合应用旋转策略时，屏幕方向不会发生变化，且接口不会抛异常。

**起始版本：** 9

<!--Device-Screen-setOrientation(orientation: Orientation, callback: AsyncCallback<void>): void--><!--Device-Screen-setOrientation(orientation: Orientation, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| orientation | [Orientation](arkts-arkui-window-orientation-e.md) | 是 | 屏幕方向。orientation值必须来自Orientation枚举方向。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当设置屏幕方向成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3. Parameter verification failed. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

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
};

// 创建虚拟屏幕
screen.createVirtualScreen(option).then((data: screen.Screen) => {
  let screenClass: screen.Screen = data;
  console.info(`Succeeded in creating the virtual screen. Data: ${JSON.stringify(data)}`);
  // 设置屏幕方向为垂直方向
  screenClass.setOrientation(screen.Orientation.VERTICAL, (err: BusinessError) => {
    const errCode: number = err.code;
    if (errCode) {
      console.error(`Failed to set the vertical orientation. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in setting the vertical orientation.');
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to create the virtual screen. Code: ${err.code}, message: ${err.message}`);
});

```

## setOrientation

```TypeScript
setOrientation(orientation: Orientation): Promise<void>
```

设置屏幕方向，使用Promise异步回调。当设置的方向符合[应用旋转策略](../../../../quick-start/module-configuration-file.md#abilities标签)（可通过配置module.json5文件中abilities标签的orientation字段设置应用旋转策略）时，屏幕方向才会发生改变；当设置方向不符合应用旋转策略时，屏幕方向不会发生变化，且接口不会抛异常。

**起始版本：** 9

<!--Device-Screen-setOrientation(orientation: Orientation): Promise<void>--><!--Device-Screen-setOrientation(orientation: Orientation): Promise<void>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| orientation | [Orientation](arkts-arkui-window-orientation-e.md) | 是 | 屏幕方向。orientation值必须来自Orientation枚举方向。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3. Parameter verification failed. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

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
};

// 创建虚拟屏幕
screen.createVirtualScreen(option).then((data: screen.Screen) => {
  let screenClass: screen.Screen = data;
  console.info(`Succeeded in creating the virtual screen. Data: ${JSON.stringify(data)}`);
  // 设置屏幕方向为垂直方向
  let promise: Promise<void> = screenClass.setOrientation(screen.Orientation.VERTICAL);
  promise.then(() => {
    console.info('Succeeded in setting the vertical orientation.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set the vertical orientation. Code: ${err.code}, message: ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to create the virtual screen. Code: ${err.code}, message: ${err.message}`);
});

```

## setOrientation

```TypeScript
setOrientation(orientation: Orientation, orientationOptions?: OrientationOptions): Promise<void>
```

设置屏幕方向

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Screen-setOrientation(orientation: Orientation, orientationOptions?: OrientationOptions): Promise<void>--><!--Device-Screen-setOrientation(orientation: Orientation, orientationOptions?: OrientationOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| orientation | [Orientation](arkts-arkui-window-orientation-e.md) | 是 | 屏幕方向。方向值必须来自方向枚举值。 |
| orientationOptions | [OrientationOptions](arkts-arkui-screen-orientationoptions-i-sys.md) | 否 | Options of setting orientation. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. Possible cause: The screen is not an external display in extended mode. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let orientationOptions : screen.OrientationOptions = {
  needAnimation: true,
  ignoreRotationLock: false,
};

let screenClass: screen.Screen | null = null;
// 获取所有屏幕对象
let screensPromise: Promise<Array<screen.Screen>> = screen.getAllScreens();
screensPromise.then((data: Array<screen.Screen>) => {
  if (data.length > 0) {
    screenClass = data[0];
    // 设置屏幕方向为垂直方向，带动画且不忽略旋转锁定
    let promise: Promise<void> = screenClass.setOrientation(screen.Orientation.VERTICAL, orientationOptions);
    promise.then(() => {
      console.info('Succeeded in setting the vertical orientation with orientationOptions.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to set the vertical orientation with orientationOptions. Code: ${err.code}, message: ${err.message}`);
    });
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to get all screens. Code: ${err.code}, message: ${err.message}`);
});

```

## setScreenActiveMode

```TypeScript
setScreenActiveMode(modeIndex: number, callback: AsyncCallback<void>): void
```

设置屏幕当前显示模式，使用callback异步回调。

**起始版本：** 9

<!--Device-Screen-setScreenActiveMode(modeIndex: long, callback: AsyncCallback<void>): void--><!--Device-Screen-setScreenActiveMode(modeIndex: long, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modeIndex | number | 是 | 模式索引。模式索引的当前值和值的范围，会根据屏幕当前分辨率、刷新率和设备硬件差异产生变化，该参数仅支持整数输入。索引为screen中[ScreenModeInfo](arkts-arkui-screen-screenmodeinfo-i-sys.md)属性的模式id。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当设置屏幕当前显示模式成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

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
};

// 创建虚拟屏幕
screen.createVirtualScreen(option).then((data: screen.Screen) => {
  let screenClass: screen.Screen = data;
  console.info(`Succeeded in creating the virtual screen. Data: ${JSON.stringify(data)}`);
  let modeIndex: number = 0;
  // 设置屏幕当前显示模式
  screenClass.setScreenActiveMode(modeIndex, (err: BusinessError) => {
    const errCode: number = err.code;
    if (errCode) {
      console.error(`Failed to set screen active mode 0. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in setting the screen active mode 0.');
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to create the virtual screen. Code: ${err.code}, message: ${err.message}`);
});

```

## setScreenActiveMode

```TypeScript
setScreenActiveMode(modeIndex: number): Promise<void>
```

设置屏幕当前显示模式，使用Promise异步回调。

**起始版本：** 9

<!--Device-Screen-setScreenActiveMode(modeIndex: long): Promise<void>--><!--Device-Screen-setScreenActiveMode(modeIndex: long): Promise<void>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modeIndex | number | 是 | 模式索引。模式索引的当前值和值的范围，会根据屏幕当前分辨率、刷新率和设备硬件差异产生变化，该参数仅支持整数输入。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

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
};

// 创建虚拟屏幕
screen.createVirtualScreen(option).then((data: screen.Screen) => {
  let screenClass: screen.Screen = data;
  console.info(`Succeeded in creating the virtual screen. Data: ${JSON.stringify(data)}`);
  let modeIndex: number = 0;
  // 设置屏幕当前显示模式
  let promise: Promise<void> = screenClass.setScreenActiveMode(modeIndex);
  promise.then(() => {
    console.info('Succeeded in setting screen active mode 0.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set screen active mode 0. Code: ${err.code}, message: ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to create the virtual screen. Code: ${err.code}, message: ${err.message}`);
});

```

## activeModeIndex

```TypeScript
readonly activeModeIndex: number
```

当前屏幕所处模式索引。模式索引的当前值和值的范围，会根据屏幕当前分辨率、刷新率和设备硬件差异产生变化。该参数为整数。

**类型：** number

**起始版本：** 9

<!--Device-Screen-readonly activeModeIndex: long--><!--Device-Screen-readonly activeModeIndex: long-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## id

```TypeScript
readonly id: number
```

屏幕的id，该参数应为整数。

**类型：** number

**起始版本：** 9

<!--Device-Screen-readonly id: long--><!--Device-Screen-readonly id: long-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## orientation

```TypeScript
readonly orientation: Orientation
```

屏幕方向。

**类型：** Orientation

**起始版本：** 9

<!--Device-Screen-readonly orientation: Orientation--><!--Device-Screen-readonly orientation: Orientation-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## parent

```TypeScript
readonly parent: number
```

屏幕所属群组的id，该参数为整数。

**类型：** number

**起始版本：** 9

<!--Device-Screen-readonly parent: long--><!--Device-Screen-readonly parent: long-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## rsId

```TypeScript
readonly rsId: number
```

屏幕端口的id，该参数为整数。

**类型：** number

**起始版本：** 21

<!--Device-Screen-readonly rsId: long--><!--Device-Screen-readonly rsId: long-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## screenType

```TypeScript
readonly screenType?: ScreenType
```

屏幕类型

**类型：** ScreenType

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Screen-readonly screenType?: ScreenType--><!--Device-Screen-readonly screenType?: ScreenType-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## serialNumber

```TypeScript
readonly serialNumber?: string
```

扩展屏幕的序列号，默认返回为空字符串。

**类型：** string

**起始版本：** 15

<!--Device-Screen-readonly serialNumber?: string--><!--Device-Screen-readonly serialNumber?: string-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## sourceMode

```TypeScript
readonly sourceMode: ScreenSourceMode
```

屏幕来源模式。

**类型：** ScreenSourceMode

**起始版本：** 10

<!--Device-Screen-readonly sourceMode: ScreenSourceMode--><!--Device-Screen-readonly sourceMode: ScreenSourceMode-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## supportedModeInfo

```TypeScript
readonly supportedModeInfo: Array<ScreenModeInfo>
```

屏幕支持的模式集合。

**类型：** Array<ScreenModeInfo>

**起始版本：** 9

<!--Device-Screen-readonly supportedModeInfo: Array<ScreenModeInfo>--><!--Device-Screen-readonly supportedModeInfo: Array<ScreenModeInfo>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

