# Macro（系统接口）

Macro继承自[MacroQuery](arkts-camera-camera-macroquery-i-sys.md)。 提供使能微距能力的接口。

**继承/实现关系：** Macro extends [MacroQuery](arkts-camera-camera-macroquery-i-sys.md)

**起始版本：** 23

<!--Device-camera-interface Macro--><!--Device-camera-interface Macro-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## enableMacro

```TypeScript
enableMacro(enabled: boolean): void
```

使能当前的微距能力。 > **说明：** > > 使用该接口前，需要先通过[isMacroSupported](arkts-camera-camera-macroquery-i-sys.md#ismacrosupported)接口查询当前设备是否支持微距能力。

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-Macro-enableMacro(enabled: boolean): void--><!--Device-Macro-enableMacro(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 是否开启微距能力。true表示开启微距能力，false表示关闭微距能力。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed.<br>**适用版本：** 12+ |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 11 - 18 |

