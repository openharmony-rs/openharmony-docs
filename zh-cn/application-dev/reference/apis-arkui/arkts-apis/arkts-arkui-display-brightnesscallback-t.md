# BrightnessCallback

```TypeScript
type BrightnessCallback<T1, T2> = (data1: T1, data2: T2) => void
```

监听屏幕亮度信息时使用的回调函数类型。

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

<!--Device-display-type BrightnessCallback<T1, T2> = (data1: T1, data2: T2) => void--><!--Device-display-type BrightnessCallback<T1, T2> = (data1: T1, data2: T2) => void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data1 | T1 | 是 | 表示displayId，类型为number。  |
| data2 | T2 | 是 | 表示brightnessInfo，类型为[BrightnessInfo]\_\_\_JSDOC\_LINK\_USD\_0\_\_\_。  |

