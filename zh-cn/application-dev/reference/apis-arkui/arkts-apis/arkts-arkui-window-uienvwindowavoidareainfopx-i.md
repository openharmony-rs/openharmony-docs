# UIEnvWindowAvoidAreaInfoPX

窗口不同类型避让区域信息组成的[环境变量](../../../ui/arkts-env-system-property.md)数据类型，每种类型避让区域单位为px。

**起始版本：** 23

<!--Device-window-interface UIEnvWindowAvoidAreaInfoPX--><!--Device-window-interface UIEnvWindowAvoidAreaInfoPX-End-->

**系统能力：** SystemCapability.Window.SessionManager

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## cutout

```TypeScript
cutout: AvoidArea
```

表示[AvoidAreaType](arkts-arkui-window-avoidareatype-e.md)为TYPE_CUTOUT类型的避让区域，单位为px。

**类型：** AvoidArea

**起始版本：** 23

<!--Device-UIEnvWindowAvoidAreaInfoPX-cutout: AvoidArea--><!--Device-UIEnvWindowAvoidAreaInfoPX-cutout: AvoidArea-End-->

**系统能力：** SystemCapability.Window.SessionManager

## keyboard

```TypeScript
keyboard: AvoidArea
```

表示[AvoidAreaType](arkts-arkui-window-avoidareatype-e.md)为TYPE_KEYBOARD类型的避让区域，单位为px。

**类型：** AvoidArea

**起始版本：** 23

<!--Device-UIEnvWindowAvoidAreaInfoPX-keyboard: AvoidArea--><!--Device-UIEnvWindowAvoidAreaInfoPX-keyboard: AvoidArea-End-->

**系统能力：** SystemCapability.Window.SessionManager

## navigationIndicator

```TypeScript
navigationIndicator: AvoidArea
```

表示[AvoidAreaType](arkts-arkui-window-avoidareatype-e.md)为TYPE_NAVIGATION_INDICATOR类型的避让区域，单位为px。

**类型：** AvoidArea

**起始版本：** 23

<!--Device-UIEnvWindowAvoidAreaInfoPX-navigationIndicator: AvoidArea--><!--Device-UIEnvWindowAvoidAreaInfoPX-navigationIndicator: AvoidArea-End-->

**系统能力：** SystemCapability.Window.SessionManager

## statusBar

```TypeScript
statusBar: AvoidArea
```

表示[AvoidAreaType](arkts-arkui-window-avoidareatype-e.md)为TYPE_SYSTEM类型的避让区域，单位为px。

**类型：** AvoidArea

**起始版本：** 23

<!--Device-UIEnvWindowAvoidAreaInfoPX-statusBar: AvoidArea--><!--Device-UIEnvWindowAvoidAreaInfoPX-statusBar: AvoidArea-End-->

**系统能力：** SystemCapability.Window.SessionManager

