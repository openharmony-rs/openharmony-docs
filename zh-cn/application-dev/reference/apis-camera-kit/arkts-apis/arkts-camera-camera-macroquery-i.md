# MacroQuery

提供查询设备是否支持相机微距拍摄的方法。

**起始版本：** 19

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
```

## isMacroSupported

```TypeScript
isMacroSupported(): boolean
```

检测当前状态下是否支持微距能力，需要在CaptureSession调用 [commitConfig](arkts-camera-camera-session-i.md#commitconfig)之后进行调用。

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回是否支持微距能力。true表示支持，false表示不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 11 - 18 |

**示例**

```TypeScript
function isMacroSupported(photoSession: camera.PhotoSession): boolean {
  let isSupported: boolean = photoSession.isMacroSupported();
  return isSupported;
}
```
