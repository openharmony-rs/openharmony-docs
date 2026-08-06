# ManualIsoQuery

Provides APIs to check whether a camera device supports manual ISO setting and obtain the ISO range supported by the device.

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-camera-interface ManualIsoQuery--><!--Device-camera-interface ManualIsoQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## getIsoRange

ArkTS-Dyn:
```TypeScript
getIsoRange(): Array<number>
```

ArkTS-Sta:
```TypeScript
getIsoRange(): Array<int>
```

Obtains the supported ISO range.

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-ManualIsoQuery-getIsoRange(): Array<int>--><!--Device-ManualIsoQuery-getIsoRange(): Array<int>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Array&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Array&lt;int&gt; | ISO range. The value range is [50, 100, ..., 6400]. The actual value depends on the |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

**示例：**

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

## getSupportedIsoRange

ArkTS-Dyn:
```TypeScript
getSupportedIsoRange(): number[]
```

ArkTS-Sta:
```TypeScript
getSupportedIsoRange(): int[]
```

Get a array of supported standard ISO sensitivity values, as defined in ISO 12232:2006.

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-ManualIsoQuery-getSupportedIsoRange(): int[]--><!--Device-ManualIsoQuery-getSupportedIsoRange(): int[]-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number[]  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int[] | The array of ISO sensitivity values. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

## isManualIsoSupported

```TypeScript
isManualIsoSupported(): boolean
```

Checks whether manual ISO setting is supported.

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-ManualIsoQuery-isManualIsoSupported(): boolean--><!--Device-ManualIsoQuery-isManualIsoSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Check result for the support of manual ISO setting. **true** if supported, **false** |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

**示例：**

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

