# ManualIsoQuery（系统接口）

Provides APIs to check whether a camera device supports manual ISO setting and obtain the ISO range supported by the device.

**起始版本：** 23

<!--Device-camera-interface ManualIsoQuery--><!--Device-camera-interface ManualIsoQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## getIsoRange

```TypeScript
getIsoRange(): Array<int>
```

Obtains the supported ISO range.

**起始版本：** 23

<!--Device-ManualIsoQuery-getIsoRange(): Array<int>--><!--Device-ManualIsoQuery-getIsoRange(): Array<int>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;int&gt; | ISO range. The value range is [50, 100, ..., 6400]. The actual value depends on the bottom-layer capability. If the operation fails, an error code defined in [CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

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

## isManualIsoSupported

```TypeScript
isManualIsoSupported(): boolean
```

Checks whether manual ISO setting is supported.

**起始版本：** 23

<!--Device-ManualIsoQuery-isManualIsoSupported(): boolean--><!--Device-ManualIsoQuery-isManualIsoSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Check result for the support of manual ISO setting. **true** if supported, **false** otherwise. If the operation fails, an error code defined in [CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

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

