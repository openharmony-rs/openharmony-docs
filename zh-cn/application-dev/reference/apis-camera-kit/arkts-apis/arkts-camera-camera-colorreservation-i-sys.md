# ColorReservation（系统接口）

ColorReservation extends [ColorReservationQuery]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ Provides API for obtaining and setting a color reservation type.

**继承/实现关系：** ColorReservation extends [ColorReservationQuery](arkts-camera-camera-colorreservationquery-i-sys.md)

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-camera-interface ColorReservation extends ColorReservationQuery--><!--Device-camera-interface ColorReservation extends ColorReservationQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## getColorReservation

```TypeScript
getColorReservation(): ColorReservationType
```

Obtains the color reservation type in use.

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-ColorReservation-getColorReservation(): ColorReservationType--><!--Device-ColorReservation-getColorReservation(): ColorReservationType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Color reservation type. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

**示例：**

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

## setColorReservation

```TypeScript
setColorReservation(type: ColorReservationType): void
```

Sets a color reservation type. Before the setting, call [getSupportedColorReservationTypes]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ to obtain the supported color reservation types.

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-ColorReservation-setColorReservation(type: ColorReservationType): void--><!--Device-ColorReservation-setColorReservation(type: ColorReservationType): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Color reservation type, which is obtained by calling [getSupportedColorReservationTypes]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;3. Parameter verification failed. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例：**

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

