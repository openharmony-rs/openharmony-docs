# WindowInfo

当前窗口的详细信息。

**起始版本：** 18

**系统能力：** SystemCapability.Window.SessionManager

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## abilityName

```TypeScript
abilityName: string
```

Ability的名称。

**类型：** string

**起始版本：** 18

**系统能力：** SystemCapability.Window.SessionManager

## bundleName

```TypeScript
bundleName: string
```

应用Bundle的名称。

**类型：** string

**起始版本：** 18

**系统能力：** SystemCapability.Window.SessionManager

## displayId

```TypeScript
displayId?: number
```

Indicates the ID of the display where the window is located.

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

## globalDisplayRect

```TypeScript
globalDisplayRect?: Rect
```

全局坐标系下的窗口尺寸。扩展屏场景下以主屏左上角为坐标原点，虚拟屏场景下以虚拟屏左上角为坐标原点。默认值：[0, 0, 0, 0]。

**类型：** Rect

**起始版本：** 20

**系统能力：** SystemCapability.Window.SessionManager

## globalRect

```TypeScript
globalRect?: Rect
```

窗口所在物理屏幕上的真实显示区域。若窗口显示时经过了缩放，获取到的是缩放后窗口在屏幕上的真实位置和大小。默认值：[0, 0, 0, 0]。

**类型：** Rect

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

## isFocused

```TypeScript
isFocused?: boolean
```

窗口是否获焦。true表示窗口获焦；false表示窗口未获焦。返回值与[isFocused()](arkts-arkui-window-window-i.md#isfocused)接口一致。

**类型：** boolean

**起始版本：** 18

**系统能力：** SystemCapability.Window.SessionManager

**示例**

```TypeScript
try {
  let focus = windowClass.isFocused();
  console.info(`Succeeded in checking whether the window is focused. Data: ${focus}`);
} catch (exception) {
  console.error(`Failed to check whether the window is focused. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## rect

```TypeScript
rect: Rect
```

窗口尺寸。

**类型：** Rect

**起始版本：** 18

**系统能力：** SystemCapability.Window.SessionManager

## windowId

```TypeScript
windowId: number
```

窗口ID。

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.Window.SessionManager

## windowStatusType

```TypeScript
windowStatusType: WindowStatusType
```

窗口模式枚举。

**类型：** WindowStatusType

**起始版本：** 18

**系统能力：** SystemCapability.Window.SessionManager
