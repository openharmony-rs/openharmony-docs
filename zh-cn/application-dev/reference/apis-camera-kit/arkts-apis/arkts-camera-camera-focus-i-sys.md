# Focus

Focus继承自[FocusQuery](arkts-camera-camera-focusquery-i.md#FocusQuery)。 对焦类，对设备对焦操作。

**继承/实现关系：** Focus extends [FocusQuery](arkts-camera-camera-focusquery-i.md#FocusQuery)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface Focus--><!--Device-camera-interface Focus-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## getFocusAssist

```TypeScript
getFocusAssist(): boolean
```

Checks whether the focus assist is enabled.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Focus-getFocusAssist(): boolean--><!--Device-Focus-getFocusAssist(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Check result for whether the focus assist is enabled. **true** if enabled, **false** otherwise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
function getFocusAssist(professionalPhotoSession: camera.ProfessionalPhotoSession): boolean {
  let isFocusAssistOpened: boolean = false;
  try {
    isFocusAssistOpened = professionalPhotoSession.getFocusAssist();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The getFocusAssist call failed. error code: ${err.code}`);
  }
  return isFocusAssistOpened;
}
```

## getFocusDriven

```TypeScript
getFocusDriven(): FocusDrivenType
```

Obtains the focus drive type in use.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Focus-getFocusDriven(): FocusDrivenType--><!--Device-Focus-getFocusDriven(): FocusDrivenType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FocusDrivenType](arkts-camera-camera-focusdriventype-e-sys.md) | Focus drive type. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getFocusDriven(session: camera.VideoSessionForSys): camera.FocusDrivenType | undefined {
  let focusDrivenType: camera.FocusDrivenType | undefined = undefined;
  try {
    focusDrivenType = session.getFocusDriven();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The getFocusDriven call failed. error code: ${err.code}`);
  }
  return focusDrivenType;
}
```

## getFocusRange

```TypeScript
getFocusRange(): FocusRangeType
```

Obtains the focus range type in use.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Focus-getFocusRange(): FocusRangeType--><!--Device-Focus-getFocusRange(): FocusRangeType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FocusRangeType](arkts-camera-camera-focusrangetype-e-sys.md) | Focus range type. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getFocusRange(session: camera.VideoSessionForSys): camera.FocusRangeType | undefined {
  let focusRangeType: camera.FocusRangeType | undefined = undefined;
  try {
    focusRangeType = session.getFocusRange();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The getFocusRange call failed. error code: ${err.code}`);
  }
  return focusRangeType;
}
```

## setFocusAssist

```TypeScript
setFocusAssist(enabled: boolean): void
```

Sets the focus assist. Before the setting, call [isFocusAssistSupported](arkts-camera-camera-focusquery-i-sys.md#isFocusAssistSupported) to check whether the device supports the focus assist.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Focus-setFocusAssist(enabled: boolean): void--><!--Device-Focus-setFocusAssist(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | Whether to enable or disable focus assist. **true** to enable, **false** otherwise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function setFocusAssist(professionalPhotoSession: camera.ProfessionalPhotoSession): void {
  try {
    professionalPhotoSession.setFocusAssist(false);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The setFocusAssist call failed. error code: ${err.code}`);
  }
}
```

## setFocusDriven

```TypeScript
setFocusDriven(type: FocusDrivenType): void
```

Sets a focus drive type. Before the setting, call [isFocusDrivenTypeSupported](arkts-camera-camera-focusquery-i-sys.md#isFocusDrivenTypeSupported) to check whether the focus drive type is supported.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Focus-setFocusDriven(type: FocusDrivenType): void--><!--Device-Focus-setFocusDriven(type: FocusDrivenType): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [FocusDrivenType](arkts-camera-camera-focusdriventype-e-sys.md) | 是 | Focus drive type. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function setFocusDriven(session: camera.VideoSessionForSys, type: camera.FocusDrivenType): void {
  try {
    session.setFocusDriven(type);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The setFocusDriven call failed. error code: ${err.code}`);
  }
}
```

## setFocusRange

```TypeScript
setFocusRange(type: FocusRangeType): void
```

Sets a focus range type. Before the setting, call [isFocusRangeTypeSupported](arkts-camera-camera-focusquery-i-sys.md#isFocusRangeTypeSupported) to check whether the focus range type is supported.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Focus-setFocusRange(type: FocusRangeType): void--><!--Device-Focus-setFocusRange(type: FocusRangeType): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [FocusRangeType](arkts-camera-camera-focusrangetype-e-sys.md) | 是 | Focus range type. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function setFocusRange(session: camera.VideoSessionForSys, type: camera.FocusRangeType): void {
  try {
    session.setFocusRange(type);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The setFocusRange call failed. error code: ${err.code}`);
  }
}
```

