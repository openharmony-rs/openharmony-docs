# RotationChangeCallback

```TypeScript
type RotationChangeCallback<T, U> = (info: T) => U
```

旋转事件通知通用回调函数。 开发者在使用时，回调函数参数类型为[RotationChangeInfo]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_，返回值类型为 [RotationChangeResult]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ \| void。

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-window-type RotationChangeCallback<T, U> = (info: T) => U--><!--Device-window-type RotationChangeCallback<T, U> = (info: T) => U-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | T | 是 | 回调函数调用时系统传入[RotationChangeInfo]\_\_\_JSDOC\_LINK\_USD\_0\_\_\_类型的参数。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| U | 回调函数需要返回[RotationChangeResult]{ |

