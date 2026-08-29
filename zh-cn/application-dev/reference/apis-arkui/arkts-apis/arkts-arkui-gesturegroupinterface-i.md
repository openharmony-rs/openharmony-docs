# GestureGroupInterface

手势识别组合，即两种及以上手势组合为复合手势，支持顺序识别、并发识别和互斥识别。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## [[Call]]

```TypeScript
(mode: GestureMode, ...gesture: GestureType[]): GestureGroupInterface
```

设置组合手势事件。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [GestureMode](arkts-arkui-gesturemode-e.md) | 是 |  |
| gesture | [GestureType](arkts-arkui-gesturetype-t.md)[] | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [GestureGroupInterface](arkts-arkui-gesturegroupinterface-i.md) |  |

## onCancel

```TypeScript
onCancel(event: () => void): GestureGroupInterface
```

手势识别成功，接收到触摸取消事件，触发回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () =&gt; void | 是 | 手势事件回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [GestureGroupInterface](arkts-arkui-gesturegroupinterface-i.md) |  |
