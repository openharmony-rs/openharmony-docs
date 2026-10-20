# Focus

```TypeScript
interface Focus extends FocusQuery
```

Focus继承自[FocusQuery](arkts-camera-camera-focusquery-i.md)。

对焦类，对设备对焦操作。

**继承/实现关系：** Focus extends [FocusQuery](arkts-camera-camera-focusquery-i.md)

**起始版本：** 11

<!--Device-camera-interface Focus extends FocusQuery--><!--Device-camera-interface Focus extends FocusQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getFocusAssist

```TypeScript
getFocusAssist(): boolean
```

查询是否已开启对焦辅助。

**起始版本：** 12

<!--Device-Focus-getFocusAssist(): boolean--><!--Device-Focus-getFocusAssist(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 查询是否已开启对焦辅助的结果。**true**表示已开启，**false**表示未开启。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

<!--Del-->
**示例**

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

<!--DelEnd-->

## getFocusDriven

```TypeScript
getFocusDriven(): FocusDrivenType
```

获取当前使用的对焦驱动类型。

**起始版本：** 15

<!--Device-Focus-getFocusDriven(): FocusDrivenType--><!--Device-Focus-getFocusDriven(): FocusDrivenType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FocusDrivenType](arkts-camera-camera-focusdriventype-e-sys.md) | 对焦驱动类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

<!--Del-->
**示例**

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

<!--DelEnd-->

## getFocusRange

```TypeScript
getFocusRange(): FocusRangeType
```

获取当前使用的对焦范围类型。

**起始版本：** 15

<!--Device-Focus-getFocusRange(): FocusRangeType--><!--Device-Focus-getFocusRange(): FocusRangeType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FocusRangeType](arkts-camera-camera-focusrangetype-e-sys.md) | 对焦范围类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

<!--Del-->
**示例**

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

<!--DelEnd-->

## setFocusAssist

```TypeScript
setFocusAssist(enabled: boolean): void
```

设置对焦辅助。设置之前，需要先调用[isFocusAssistSupported](arkts-camera-camera-focusquery-i-sys.md#isfocusassistsupported)检测设备是否支持对焦辅助。

**起始版本：** 12

<!--Device-Focus-setFocusAssist(enabled: boolean): void--><!--Device-Focus-setFocusAssist(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 是否开启或关闭对焦辅助。**true**表示开启，**false**表示关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

<!--Del-->
**示例**

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

<!--DelEnd-->

## setFocusDriven

```TypeScript
setFocusDriven(type: FocusDrivenType): void
```

设置对焦驱动类型。设置之前，需要先调用[isFocusDrivenTypeSupported](arkts-camera-camera-focusquery-i-sys.md#isfocusdriventypesupported)检测是否支持该对焦驱动类型。

**起始版本：** 15

<!--Device-Focus-setFocusDriven(type: FocusDrivenType): void--><!--Device-Focus-setFocusDriven(type: FocusDrivenType): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [FocusDrivenType](arkts-camera-camera-focusdriventype-e-sys.md) | 是 | 对焦驱动类型。 |

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

<!--DelEnd-->

## setFocusRange

```TypeScript
setFocusRange(type: FocusRangeType): void
```

设置对焦范围类型。设置之前，需要先调用[isFocusRangeTypeSupported](arkts-camera-camera-focusquery-i-sys.md#isfocusrangetypesupported)检测是否支持该对焦范围类型。

**起始版本：** 15

<!--Device-Focus-setFocusRange(type: FocusRangeType): void--><!--Device-Focus-setFocusRange(type: FocusRangeType): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [FocusRangeType](arkts-camera-camera-focusrangetype-e-sys.md) | 是 | 对焦范围类型。 |

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

<!--DelEnd-->
