# SubWindowOptions

子窗口创建参数。

**起始版本：** 11

<!--Device-window-interface SubWindowOptions--><!--Device-window-interface SubWindowOptions-End-->

**系统能力：** SystemCapability.Window.SessionManager

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## decorEnabled

```TypeScript
decorEnabled: boolean
```

子窗口是否显示装饰。true表示子窗口显示装饰，false表示子窗口不显示装饰。

**类型：** boolean

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SubWindowOptions-decorEnabled: boolean--><!--Device-SubWindowOptions-decorEnabled: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

## isModal

```TypeScript
isModal?: boolean
```

子窗口是否启用模态属性。true表示子窗口启用模态属性，false表示子窗口禁用模态属性。不设置，则默认为false。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SubWindowOptions-isModal?: boolean--><!--Device-SubWindowOptions-isModal?: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

## maximizeSupported

```TypeScript
maximizeSupported?: boolean
```

子窗口是否支持最大化特性。true表示子窗口支持最大化，false表示子窗口不支持最大化。不设置，则默认为false。

该参数在支持并处于[自由窗口](docroot://windowmanager/window-terminology.md#自由窗口)状态的设备上可正常调用；在不支持[自由窗口](docroot://windowmanager/window-terminology.md#自由窗口)状态的设备上，作为入参使用时，对应接口不生效不报错；在支持但不处于[自由窗口](docroot://windowmanager/window-terminology.md#自由窗口)状态的设备上，作为入参使用时，对应接口不生效不报错，切换到[自由窗口](docroot://windowmanager/window-terminology.md#自由窗口)状态后生效。

**类型：** boolean

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-SubWindowOptions-maximizeSupported?: boolean--><!--Device-SubWindowOptions-maximizeSupported?: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

## modalityType

```TypeScript
modalityType?: ModalityType
```

子窗口模态类型，仅当子窗口启用模态属性时生效。不设置，则默认为WINDOW_MODALITY。

**类型：** ModalityType

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-SubWindowOptions-modalityType?: ModalityType--><!--Device-SubWindowOptions-modalityType?: ModalityType-End-->

**系统能力：** SystemCapability.Window.SessionManager

## outlineEnabled

```TypeScript
outlineEnabled?: boolean
```

子窗口是否显示描边。true表示子窗口显示描边，false表示子窗口不显示描边。不设置，则默认为false。

该参数在2in1设备、其他设备的电脑模式中可正常调用，在其他设备和其他模式中作为入参使用时，对应接口不生效不报错。

**类型：** boolean

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SubWindowOptions-outlineEnabled?: boolean--><!--Device-SubWindowOptions-outlineEnabled?: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

## title

```TypeScript
title: string
```

子窗口标题。标题显示区域最右端不超过系统三键区域最左端，超过部分以省略号表示。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SubWindowOptions-title: string--><!--Device-SubWindowOptions-title: string-End-->

**系统能力：** SystemCapability.Window.SessionManager

## windowRect

```TypeScript
windowRect?: Rect
```

子窗口矩形区域，其中子窗口存在大小限制，具体参考[resize()](arkts-arkui-window-window-i.md#resize-1)方法。不设置且未调用[showWindow()](arkts-arkui-window-window-i.md#showwindow-1)显示前，则默认为{left: 0,top: 0, width: 0, height: 0}。具体参考[设置应用子窗口](docroot://windowmanager/application-window-stage.md#设置应用子窗口)开发指南。

**类型：** Rect

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SubWindowOptions-windowRect?: Rect--><!--Device-SubWindowOptions-windowRect?: Rect-End-->

**系统能力：** SystemCapability.Window.SessionManager

## zLevel

```TypeScript
zLevel?: number
```

子窗口层级级别，仅当子窗口未启用模态属性，即未设置isModal时生效。该参数是整数，取值范围为[-10000, 10000]，浮点数输入将向下取整。不设置，则默认为0。

**类型：** number

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SubWindowOptions-zLevel?: int--><!--Device-SubWindowOptions-zLevel?: int-End-->

**系统能力：** SystemCapability.Window.SessionManager

## zLevelAboveParentLoosened

```TypeScript
zLevelAboveParentLoosened?: boolean
```

标识解除子窗在父窗口的层级限制

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SubWindowOptions-zLevelAboveParentLoosened?: boolean--><!--Device-SubWindowOptions-zLevelAboveParentLoosened?: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

