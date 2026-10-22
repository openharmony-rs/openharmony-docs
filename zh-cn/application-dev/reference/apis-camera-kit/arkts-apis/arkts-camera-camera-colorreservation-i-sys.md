# ColorReservation（系统接口）

```TypeScript
interface ColorReservation extends ColorReservationQuery
```

ColorReservation 继承 [ColorReservationQuery](arkts-camera-camera-colorreservationquery-i-sys.md)提供获取和设置色彩保留类型的接口。

**继承/实现关系：** ColorReservation extends [ColorReservationQuery](arkts-camera-camera-colorreservationquery-i-sys.md)

**起始版本：** 15

<!--Device-camera-interface ColorReservation extends ColorReservationQuery--><!--Device-camera-interface ColorReservation extends ColorReservationQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getColorReservation

```TypeScript
getColorReservation(): ColorReservationType
```

获取当前使用的色彩保留类型。

**起始版本：** 15

<!--Device-ColorReservation-getColorReservation(): ColorReservationType--><!--Device-ColorReservation-getColorReservation(): ColorReservationType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorReservationType](arkts-camera-camera-colorreservationtype-e-sys.md) | 色彩保留类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getColorReservation(session: camera.VideoSessionForSys): camera.ColorReservationType | undefined {
  let colorReservation: camera.ColorReservationType | undefined = undefined;
  try {
    colorReservation = session.getColorReservation();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The setColorReservation call failed. error code: ${err.code}`);
  }
  return colorReservation;
}
```

<!--DelEnd-->

## setColorReservation

```TypeScript
setColorReservation(type: ColorReservationType): void
```

设置色彩保留类型。设置前，请先调用[getSupportedColorReservationTypes](arkts-camera-camera-colorreservationquery-i-sys.md#getsupportedcolorreservationtypes)获取支持的色彩保留类型。

**起始版本：** 15

<!--Device-ColorReservation-setColorReservation(type: ColorReservationType): void--><!--Device-ColorReservation-setColorReservation(type: ColorReservationType): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [ColorReservationType](arkts-camera-camera-colorreservationtype-e-sys.md) | 是 | 色彩保留类型，通过调用[getSupportedColorReservationTypes](arkts-camera-camera-colorreservationquery-i-sys.md#getsupportedcolorreservationtypes) 获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:         1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;         3. Parameter verification failed. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function setColorReservation(session: camera.VideoSessionForSys, type: camera.ColorReservationType): void {
  try {
    session.setColorReservation(type);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The setColorReservation call failed. error code: ${err.code}`);
  }
}
```

<!--DelEnd-->
