# Display

屏幕实例。描述Display对象的属性和方法。

下列API示例中都需先使用[getAllDisplays()](arkts-arkui-display-getalldisplays-f.md#getalldisplays-1)、[getDefaultDisplaySync()](arkts-arkui-display-getdefaultdisplaysync-f.md#getdefaultdisplaysync-1)中的任一方法获取到Display实例，再通过此实例调用对应方法。

**起始版本：** 7

<!--Device-display-interface Display--><!--Device-display-interface Display-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## 导入模块

```TypeScript
import { display } from '@kit.ArkUI';
```

## getAvailableArea

```TypeScript
getAvailableArea(): Promise<Rect>
```

获取当前设备屏幕的可用区域，使用Promise异步回调。

可用区域是扣除系统UI（如状态栏、Dock栏）后，可供应用程序自由使用的区域。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Display-getAvailableArea(): Promise<Rect>--><!--Device-Display-getAvailableArea(): Promise<Rect>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Rect> | Promise对象。返回当前屏幕可用矩形区域。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. Possible cause:1. This display is abnormal.2. Internal task error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let displayClass: display.Display | null = null;
try {
  displayClass = display.getDefaultDisplaySync();
  let promise = displayClass.getAvailableArea();
  promise.then((data) => {
    console.info(`Succeeded in getting the available area in this display. data: ${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get the available area in this display. Code: ${err.code}, message: ${err.message}`);
  })
} catch (exception) {
  console.error(`Failed to obtain the default display object. Code: ${exception.code}, message: ${exception.message}`);
}

```

## getCutoutInfo

```TypeScript
getCutoutInfo(callback: AsyncCallback<CutoutInfo>): void
```

获取挖孔屏、刘海屏、瀑布屏等不可用屏幕区域信息。使用callback异步回调。建议应用布局规避该区域。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Display-getCutoutInfo(callback: AsyncCallback<CutoutInfo>): void--><!--Device-Display-getCutoutInfo(callback: AsyncCallback<CutoutInfo>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<CutoutInfo> | 是 | 回调函数。返回不可用屏幕区域对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. Possible cause:1. This display is abnormal.2. Internal task error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let displayClass: display.Display | null = null;
displayClass = display.getDefaultDisplaySync();

displayClass.getCutoutInfo((err: BusinessError, data: display.CutoutInfo) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to get cutoutInfo. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting cutoutInfo. Data: ${JSON.stringify(data)}`);
});

```

## getCutoutInfo

```TypeScript
getCutoutInfo(): Promise<CutoutInfo>
```

获取挖孔屏、刘海屏、瀑布屏等不可用屏幕区域信息。使用Promise异步回调。建议应用布局规避该区域。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Display-getCutoutInfo(): Promise<CutoutInfo>--><!--Device-Display-getCutoutInfo(): Promise<CutoutInfo>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<CutoutInfo> | Promise对象。返回描述不可用屏幕区域的CutoutInfo对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let displayClass: display.Display | null = null;
displayClass = display.getDefaultDisplaySync();
let promise: Promise<display.CutoutInfo> = displayClass.getCutoutInfo();
promise.then((data: display.CutoutInfo) => {
  console.info(`Succeeded in getting cutoutInfo. Data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get cutoutInfo. Code: ${err.code}, message: ${err.message}`);
});

```

## getDisplayCapability

```TypeScript
getDisplayCapability(): string
```

Get current display capability, including foldstatus, displaymode, rotation, and orientation information.

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Display-getDisplayCapability(): string--><!--Device-Display-getDisplayCapability(): string-End-->

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Indicates the current foldstatus, displaymode, rotation, and orientation information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Function getDisplayCapability can not work correctly due to limited device capabilities. |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

## getLiveCreaseRegion

```TypeScript
getLiveCreaseRegion(): FoldCreaseRegion
```

获取当前显示模式下的实时折痕区域。

**起始版本：** 20

<!--Device-Display-getLiveCreaseRegion(): FoldCreaseRegion--><!--Device-Display-getLiveCreaseRegion(): FoldCreaseRegion-End-->

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FoldCreaseRegion](arkts-arkui-display-foldcreaseregion-i.md) | 返回设备在当前显示模式下的折叠折痕区域。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
let displayClass: display.Display | null = null;
try {
  displayClass = display.getDefaultDisplaySync();
  let data: display.FoldCreaseRegion = displayClass.getLiveCreaseRegion();
  console.info(`Succeeded in getting the live crease region. Data: ${JSON.stringify(data)}`);
} catch (exception) {
  console.error(`Failed to get the live crease region. Code: ${exception.code}, message: ${exception.message}`);
}

```

## getRoundedCorner

```TypeScript
getRoundedCorner(): Array<RoundedCorner>
```

获取屏幕的圆角信息。屏幕圆角信息由产品配置决定，只有配置了屏幕圆角半径的物理屏幕才能返回圆角信息，否则返回空数组，虚拟屏同样返回空数组。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Display-getRoundedCorner(): Array<RoundedCorner>--><!--Device-Display-getRoundedCorner(): Array<RoundedCorner>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<RoundedCorner> | 返回当前屏幕的圆角信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let displayClass: display.Display | null = null;
try {
  displayClass = display.getDefaultDisplaySync();
  let data = displayClass.getRoundedCorner();
  console.info(`Succeeded in getting rounded corner. Data: ${JSON.stringify(data)}`);
} catch (error) {
  console.error(`Failed to get rounded corner. Code: ${error.code}, message: ${error.message}`);
}

```

## off('availableAreaChange')

```TypeScript
off(type: 'availableAreaChange', callback?: Callback<Rect>): void
```

关闭当前设备屏幕可用区域变化的监听。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Display-off(type: 'availableAreaChange', callback?: Callback<Rect>): void--><!--Device-Display-off(type: 'availableAreaChange', callback?: Callback<Rect>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'availableAreaChange' | 是 | 监听事件，固定为'availableAreaChange'，表示屏幕可用区域变更。 |
| callback | [Callback](../arkts-components/arkts-arkui-common-callback-i.md)<Rect> | 否 | 需要取消注册的回调函数。返回改变后的可用区域。若无此参数，则取消注册屏幕可用区域变化监听的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let callback: Callback<display.Rect> = (data: display.Rect) => {
  console.info(`Listening enabled. Data: ${JSON.stringify(data)}`);
};
let displayClass: display.Display | null = null;
try {
  displayClass = display.getDefaultDisplaySync();
  displayClass.off('availableAreaChange', callback);
} catch (exception) {
  console.error(`Failed to unregister callback. Code: ${exception.code}, message: ${exception.message}`);
}

```

## on('availableAreaChange')

```TypeScript
on(type: 'availableAreaChange', callback: Callback<Rect>): void
```

开启当前设备屏幕可用区域的监听。当屏幕旋转、进入/退出自由多窗模式、设置Dock栏/状态栏等系统控件可见性变化时，触发回调函数，返回可用区域信息。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Display-on(type: 'availableAreaChange', callback: Callback<Rect>): void--><!--Device-Display-on(type: 'availableAreaChange', callback: Callback<Rect>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'availableAreaChange' | 是 | 监听事件。固定为'availableAreaChange'，表示屏幕可用区域变更。 |
| callback | [Callback](../arkts-components/arkts-arkui-common-callback-i.md)<Rect> | 是 | 回调函数。返回改变后的可用区域。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let callback: Callback<display.Rect> = (data: display.Rect) => {
  console.info(`Listening enabled. Data: ${JSON.stringify(data)}`);
};
let displayClass: display.Display | null = null;
try {
  displayClass = display.getDefaultDisplaySync();
  displayClass.on('availableAreaChange', callback);
} catch (exception) {
  console.error(`Failed to register callback. Code: ${exception.code}, message: ${exception.message}`);
}

```

## alive

```TypeScript
alive: boolean
```

显示设备的启用状态，表示设备是否处于正常运行状态。true表示已启用，处于正常运行状态；false表示未启用，未处于正常运行状态。

SystemCapability.WindowManager.WindowManager.Core

**类型：** boolean

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Display-alive: boolean--><!--Device-Display-alive: boolean-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## availableHeight

```TypeScript
availableHeight: number
```

显示设备的可用区域高度，单位为px，该参数为大于0的整数。

SystemCapability.WindowManager.WindowManager.Core

该接口在2in1设备、Tablet设备中可正常调用；在其他设备中不可用，请通过height属性获取当前设备屏幕的可用区域高度。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Display-availableHeight: long--><!--Device-Display-availableHeight: long-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## availableWidth

```TypeScript
availableWidth: number
```

显示设备的可用区域宽度，单位为px，该参数为大于0的整数。

SystemCapability.WindowManager.WindowManager.Core

该接口在2in1设备、Tablet设备中可正常调用；在其他设备中不可用，请通过width属性获取当前设备屏幕的可用区域宽度。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Display-availableWidth: long--><!--Device-Display-availableWidth: long-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## colorSpaces

```TypeScript
colorSpaces: Array<colorSpaceManager.ColorSpace>
```

显示设备支持的所有色域类型。

SystemCapability.WindowManager.WindowManager.Core

**类型：** Array<colorSpaceManager.ColorSpace>

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Display-colorSpaces: Array<colorSpaceManager.ColorSpace>--><!--Device-Display-colorSpaces: Array<colorSpaceManager.ColorSpace>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## densityDPI

```TypeScript
densityDPI: number
```

显示设备的物理像素密度，表示每英寸上的像素点数。该参数为浮点数，单位为px。一般取值160.0、480.0等，实际能取到的值取决于不同设备设置里提供的可选值。

SystemCapability.WindowManager.WindowManager.Core

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Display-densityDPI: double--><!--Device-Display-densityDPI: double-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## densityPixels

```TypeScript
densityPixels: number
```

显示设备逻辑像素的密度，代表物理像素与逻辑像素的缩放系数，计算方式为：![densityPixels](../../../../reference/apis-arkui/figures/densityPixels.jpg)

该参数为浮点数，受densityDPI范围限制，取值范围在[0.5，4.0]。一般取值1.0、3.0等，实际取值取决于不同设备提供的densityDPI。

SystemCapability.WindowManager.WindowManager.Core

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Display-densityPixels: double--><!--Device-Display-densityPixels: double-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## hdrFormats

```TypeScript
hdrFormats: Array<hdrCapability.HDRFormat>
```

显示设备支持的所有HDR格式。

SystemCapability.WindowManager.WindowManager.Core

**类型：** Array<hdrCapability.HDRFormat>

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Display-hdrFormats: Array<hdrCapability.HDRFormat>--><!--Device-Display-hdrFormats: Array<hdrCapability.HDRFormat>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## height

```TypeScript
height: number
```

显示设备的屏幕高度，单位为px，该参数为整数。

SystemCapability.WindowManager.WindowManager.Core

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Display-height: long--><!--Device-Display-height: long-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## id

```TypeScript
id: number
```

显示设备的屏幕ID，该参数为大于等于0的整数。

SystemCapability.WindowManager.WindowManager.Core

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Display-id: long--><!--Device-Display-id: long-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## name

```TypeScript
name: string
```

显示设备的名称。

SystemCapability.WindowManager.WindowManager.Core

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Display-name: string--><!--Device-Display-name: string-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## orientation

```TypeScript
orientation: Orientation
```

表示显示设备当前显示的方向。

SystemCapability.WindowManager.WindowManager.Core

**类型：** Orientation

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Display-orientation: Orientation--><!--Device-Display-orientation: Orientation-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## refreshRate

```TypeScript
refreshRate: number
```

显示设备当前采用的刷新率，该参数为整数，单位为Hz。

SystemCapability.WindowManager.WindowManager.Core

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Display-refreshRate: int--><!--Device-Display-refreshRate: int-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## rotation

```TypeScript
rotation: number
```

显示设备的屏幕顺时针旋转角度。

值为0时，表示显示设备屏幕顺时针旋转为0°，表示显示设备的标准显示方向；

值为1时，表示显示设备屏幕顺时针旋转为90°；

值为2时，表示显示设备屏幕顺时针旋转为180°；

值为3时，表示显示设备屏幕顺时针旋转为270°。

SystemCapability.WindowManager.WindowManager.Core

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Display-rotation: int--><!--Device-Display-rotation: int-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## scaledDensity

```TypeScript
scaledDensity: number
```

显示设备上的字体的缩放因子。该参数为浮点数，通常与densityPixels相同。

SystemCapability.WindowManager.WindowManager.Core

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Display-scaledDensity: double--><!--Device-Display-scaledDensity: double-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## screenShape

```TypeScript
screenShape?: ScreenShape
```

显示设备的屏幕形状，默认值为RECTANGLE。

SystemCapability.WindowManager.WindowManager.Core

**类型：** ScreenShape

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Display-screenShape?: ScreenShape--><!--Device-Display-screenShape?: ScreenShape-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## sourceMode

```TypeScript
sourceMode?: DisplaySourceMode
```

显示设备的显示模式枚举，默认值为DisplaySourceMode.NONE。

SystemCapability.Window.SessionManager

**类型：** DisplaySourceMode

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-Display-sourceMode?: DisplaySourceMode--><!--Device-Display-sourceMode?: DisplaySourceMode-End-->

**系统能力：** SystemCapability.Window.SessionManager

## state

```TypeScript
state: DisplayState
```

显示设备的状态。

SystemCapability.WindowManager.WindowManager.Core

**类型：** DisplayState

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Display-state: DisplayState--><!--Device-Display-state: DisplayState-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## supportedRefreshRates

```TypeScript
supportedRefreshRates?: Array<number>
```

显示设备支持的所有刷新率，从小到大排序。刷新率值为正整数，单位为Hz。默认为空。

SystemCapability.Window.SessionManager

**类型：** Array<number>

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-Display-supportedRefreshRates?: Array<int>--><!--Device-Display-supportedRefreshRates?: Array<int>-End-->

**系统能力：** SystemCapability.Window.SessionManager

## width

```TypeScript
width: number
```

显示设备的屏幕宽度，单位为px，该参数为整数。

SystemCapability.WindowManager.WindowManager.Core

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Display-width: long--><!--Device-Display-width: long-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## x

```TypeScript
x?: number
```

显示设备左上角相对于原点的y轴坐标，原点为主屏左上角，单位为px，该参数为整数，默认值为0。仅DisplaySourceMode为MAIN和EXTEND时返回实际值，其余默认返回默认值0。

SystemCapability.Window.SessionManager

**类型：** number

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-Display-x?: long--><!--Device-Display-x?: long-End-->

**系统能力：** SystemCapability.Window.SessionManager

## xDPI

```TypeScript
xDPI: number
```

x轴方向中每英寸屏幕的确切物理像素值，该参数为浮点数。

SystemCapability.WindowManager.WindowManager.Core

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Display-xDPI: double--><!--Device-Display-xDPI: double-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## y

```TypeScript
y?: number
```

显示设备左上角相对于原点的y轴坐标，原点为主屏左上角，单位为px，该参数为整数，默认值为0。仅DisplaySourceMode为MAIN和EXTEND时返回实际值，其余默认返回默认值0。

SystemCapability.Window.SessionManager

**类型：** number

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-Display-y?: long--><!--Device-Display-y?: long-End-->

**系统能力：** SystemCapability.Window.SessionManager

## yDPI

```TypeScript
yDPI: number
```

y轴方向中每英寸屏幕的确切物理像素值，该参数为浮点数。

SystemCapability.WindowManager.WindowManager.Core

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Display-yDPI: double--><!--Device-Display-yDPI: double-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

