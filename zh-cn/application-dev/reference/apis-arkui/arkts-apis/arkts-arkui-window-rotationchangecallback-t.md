# RotationChangeCallback

```TypeScript
type RotationChangeCallback<T, U> = (info: T) => U
```

旋转事件通知通用回调函数。

开发者在使用时，回调函数参数类型为[RotationChangeInfo](arkts-arkui-window-rotationchangeinfo-i.md#RotationChangeInfo)，返回值类型为
[RotationChangeResult](arkts-arkui-window-rotationchangeresult-i.md#RotationChangeResult) \| void。

**起始版本：** 19

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | T | 是 | 回调函数调用时系统传入[RotationChangeInfo](arkts-arkui-window-rotationchangeinfo-i.md#RotationChangeInfo)类型的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| U | 回调函数需要返回[RotationChangeResult](arkts-arkui-window-rotationchangeresult-i.md#RotationChangeResult) \| void类型的返回值。 |

