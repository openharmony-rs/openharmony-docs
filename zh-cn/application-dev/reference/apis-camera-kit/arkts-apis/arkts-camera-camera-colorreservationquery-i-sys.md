# ColorReservationQuery（系统接口）

```TypeScript
interface ColorReservationQuery
```

提供查询设备支持的色彩保留类型的接口。

**起始版本：** 15

<!--Device-camera-interface ColorReservationQuery--><!--Device-camera-interface ColorReservationQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getSupportedColorReservationTypes

```TypeScript
getSupportedColorReservationTypes(): Array<ColorReservationType>
```

获取支持的色彩保留类型。

**起始版本：** 15

<!--Device-ColorReservationQuery-getSupportedColorReservationTypes(): Array<ColorReservationType>--><!--Device-ColorReservationQuery-getSupportedColorReservationTypes(): Array<ColorReservationType>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[ColorReservationType](arkts-camera-camera-colorreservationtype-e-sys.md)&gt; | 支持的色彩保留类型数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getSupportedColorReservationTypes(session: camera.VideoSessionForSys): Array<camera.ColorReservationType> {
  let colorReservationTypes: Array<camera.ColorReservationType> = [];
  try {
    colorReservationTypes = session.getSupportedColorReservationTypes();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The getSupportedColorReservationTypes call failed. error code: ${err.code}`);
  }
  return colorReservationTypes;
}
```

<!--DelEnd-->
