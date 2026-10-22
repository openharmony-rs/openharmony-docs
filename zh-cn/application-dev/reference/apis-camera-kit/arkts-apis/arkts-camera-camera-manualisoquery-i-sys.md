# ManualIsoQuery（系统接口）

```TypeScript
interface ManualIsoQuery
```

提供了查询相机设备是否支持手动ISO设置以及获取设备支持的ISO范围的方法。

**起始版本：** 24

<!--Device-camera-interface ManualIsoQuery--><!--Device-camera-interface ManualIsoQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getIsoRange

```TypeScript
getIsoRange(): Array<number>
```

获取支持的ISO范围。

**起始版本：** 12

<!--Device-ManualIsoQuery-getIsoRange(): Array<int>--><!--Device-ManualIsoQuery-getIsoRange(): Array<int>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;number&gt; | ISO范围。取值范围为[50, 100, ..., 6400]，实际值取决于底层能力。接口调用失败会返回错误码，错误码定义见[CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getIsoRange(professionalPhotoSession: camera.ProfessionalPhotoSession): Array<number> {
  let isoRange: Array<number> = [];
  try {
    isoRange = professionalPhotoSession.getIsoRange();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The getIsoRange call failed. error code: ${err.code}`);
  }
  return isoRange;
}
```

<!--DelEnd-->

## isManualIsoSupported

```TypeScript
isManualIsoSupported(): boolean
```

检测是否支持手动ISO设置。

**起始版本：** 12

<!--Device-ManualIsoQuery-isManualIsoSupported(): boolean--><!--Device-ManualIsoQuery-isManualIsoSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检测是否支持手动ISO设置的结果。**true**表示支持，**false**表示不支持。接口调用失败会返回错误码，错误码定义见[CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function isManualIsoSupported(professionalPhotoSession: camera.ProfessionalPhotoSession): boolean {
  let status: boolean = false;
  try {
    status = professionalPhotoSession.isManualIsoSupported();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The isManualIsoSupported call failed. error code: ${err.code}`);
  }
  return status;
}
```

<!--DelEnd-->
