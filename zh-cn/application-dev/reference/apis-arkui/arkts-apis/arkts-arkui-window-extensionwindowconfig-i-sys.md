# ExtensionWindowConfig（系统接口）

创建扩展窗口时需要配置的参数。

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

<!--Device-window-interface ExtensionWindowConfig--><!--Device-window-interface ExtensionWindowConfig-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## subWindowOptions

```TypeScript
subWindowOptions?: SubWindowOptions
```

创建子窗口的参数。无默认参数，当windowAttribute配置为SUB\_WINDOW时必选，否则会导致窗口创建失败。

**类型：** SubWindowOptions

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtensionWindowConfig-subWindowOptions?: SubWindowOptions--><!--Device-ExtensionWindowConfig-subWindowOptions?: SubWindowOptions-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## systemWindowOptions

```TypeScript
systemWindowOptions?: SystemWindowOptions
```

创建系统窗口的参数。无默认参数，当windowAttribute配置为SYSTEM\_WINDOW时必选，否则会导致窗口创建失败。

**类型：** SystemWindowOptions

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtensionWindowConfig-systemWindowOptions?: SystemWindowOptions--><!--Device-ExtensionWindowConfig-systemWindowOptions?: SystemWindowOptions-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## windowAttribute

```TypeScript
windowAttribute: ExtensionWindowAttribute
```

窗口的属性。用于配置创建的窗口是子窗口还是系统窗口。当windowAttribute配置为SUB\_WINDOW时须配置subWindowOptions，当windowAttribute配置为SYSTEM\_WINDOW时须配置 systemWindowOptions，否则创建窗口失败。

**类型：** ExtensionWindowAttribute

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtensionWindowConfig-windowAttribute: ExtensionWindowAttribute--><!--Device-ExtensionWindowConfig-windowAttribute: ExtensionWindowAttribute-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## windowName

```TypeScript
windowName: string
```

窗口名。

**类型：** string

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtensionWindowConfig-windowName: string--><!--Device-ExtensionWindowConfig-windowName: string-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## windowRect

```TypeScript
windowRect: Rect
```

窗口矩形区域。

**类型：** Rect

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtensionWindowConfig-windowRect: Rect--><!--Device-ExtensionWindowConfig-windowRect: Rect-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

