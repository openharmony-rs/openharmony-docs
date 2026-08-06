# WindowInfo

当前窗口的详细信息。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-window-interface WindowInfo--><!--Device-window-interface WindowInfo-End-->

**系统能力：** SystemCapability.Window.SessionManager

## abilityName

```TypeScript
abilityName: string
```

Ability的名称。

**类型：** string

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-WindowInfo-abilityName: string--><!--Device-WindowInfo-abilityName: string-End-->

**系统能力：** SystemCapability.Window.SessionManager

## bundleName

```TypeScript
bundleName: string
```

应用Bundle的名称。

**类型：** string

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-WindowInfo-bundleName: string--><!--Device-WindowInfo-bundleName: string-End-->

**系统能力：** SystemCapability.Window.SessionManager

## displayId

```TypeScript
displayId?: int
```

Indicates the ID of the display where the window is located.

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowInfo-displayId?: int--><!--Device-WindowInfo-displayId?: int-End-->

**系统能力：** SystemCapability.Window.SessionManager

## globalDisplayRect

```TypeScript
globalDisplayRect?: Rect
```

全局坐标系下的窗口尺寸。扩展屏场景下以主屏左上角为坐标原点，虚拟屏场景下以虚拟屏左上角为坐标原点。默认值：[0, 0, 0, 0]。

**类型：** Rect

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-WindowInfo-globalDisplayRect?: Rect--><!--Device-WindowInfo-globalDisplayRect?: Rect-End-->

**系统能力：** SystemCapability.Window.SessionManager

## globalRect

```TypeScript
globalRect?: Rect
```

窗口所在物理屏幕上的真实显示区域。若窗口显示时经过了缩放，获取到的是缩放后窗口在屏幕上的真实位置和大小。默认值：[0, 0, 0, 0]。

**类型：** Rect

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowInfo-globalRect?: Rect--><!--Device-WindowInfo-globalRect?: Rect-End-->

**系统能力：** SystemCapability.Window.SessionManager

## isFocused

```TypeScript
isFocused?: boolean
```

窗口是否获焦。true表示窗口获焦；false表示窗口未获焦。返回值与[isFocused()]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_接口一致。

**类型：** boolean

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

<!--Device-WindowInfo-isFocused?: boolean--><!--Device-WindowInfo-isFocused?: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

## rect

```TypeScript
rect: Rect
```

窗口尺寸。

**类型：** Rect

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-WindowInfo-rect: Rect--><!--Device-WindowInfo-rect: Rect-End-->

**系统能力：** SystemCapability.Window.SessionManager

## windowId

```TypeScript
windowId: int
```

窗口ID。

**类型：** int

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-WindowInfo-windowId: int--><!--Device-WindowInfo-windowId: int-End-->

**系统能力：** SystemCapability.Window.SessionManager

## windowStatusType

```TypeScript
windowStatusType: WindowStatusType
```

窗口模式枚举。

**类型：** WindowStatusType

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-WindowInfo-windowStatusType: WindowStatusType--><!--Device-WindowInfo-windowStatusType: WindowStatusType-End-->

**系统能力：** SystemCapability.Window.SessionManager

