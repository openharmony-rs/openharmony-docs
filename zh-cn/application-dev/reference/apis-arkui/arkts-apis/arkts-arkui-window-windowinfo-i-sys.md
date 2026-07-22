# WindowInfo（系统接口）

当前窗口的详细信息。

**起始版本：** 18

<!--Device-window-interface WindowInfo--><!--Device-window-interface WindowInfo-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

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

<!--Device-WindowInfo-abilityName: string--><!--Device-WindowInfo-abilityName: string-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName: string
```

应用Bundle的名称。

**类型：** string

**起始版本：** 18

<!--Device-WindowInfo-bundleName: string--><!--Device-WindowInfo-bundleName: string-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## isFocused

```TypeScript
isFocused?: boolean
```

窗口是否获焦。true表示窗口获焦；false表示窗口未获焦。返回值与[isFocused()](arkts-arkui-window-window-i.md#isfocused)接口一致。

**类型：** boolean

**起始版本：** 18

<!--Device-WindowInfo-isFocused?: boolean--><!--Device-WindowInfo-isFocused?: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## rect

```TypeScript
rect: Rect
```

窗口尺寸。

**类型：** Rect

**起始版本：** 18

<!--Device-WindowInfo-rect: Rect--><!--Device-WindowInfo-rect: Rect-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## windowId

```TypeScript
windowId: number
```

窗口ID。

**类型：** number

**起始版本：** 18

<!--Device-WindowInfo-windowId: int--><!--Device-WindowInfo-windowId: int-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## windowStatusType

```TypeScript
windowStatusType: WindowStatusType
```

窗口模式枚举。

**类型：** WindowStatusType

**起始版本：** 18

<!--Device-WindowInfo-windowStatusType: WindowStatusType--><!--Device-WindowInfo-windowStatusType: WindowStatusType-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

