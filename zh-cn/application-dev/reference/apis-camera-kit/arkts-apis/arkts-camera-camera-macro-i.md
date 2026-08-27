# Macro

Macro继承自[MacroQuery](arkts-camera-camera-macroquery-i.md)。提供使能微距能力的接口。

**继承/实现关系：** Macro extends [MacroQuery](arkts-camera-camera-macroquery-i.md)

**起始版本：** 19

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
```

## enableMacro

```TypeScript
enableMacro(enabled: boolean): void
```

使能当前的微距能力。

> **说明：**
> 
> 使用该接口前，需要先通过[isMacroSupported](arkts-camera-camera-macroquery-i.md#ismacrosupported)接口查询当前设备是否支持微距能力。

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 是否开启微距能力。true表示开启微距能力，false表示关闭微距能力。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 11 - 18 |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed.<br>**适用版本：** 12+ |

**示例**

```TypeScript
function enableMacro(photoSession: camera.PhotoSession): void {
  let isSupported: boolean = photoSession.isMacroSupported();
  if (isSupported) {
    photoSession.enableMacro(true);
  }
}
```
