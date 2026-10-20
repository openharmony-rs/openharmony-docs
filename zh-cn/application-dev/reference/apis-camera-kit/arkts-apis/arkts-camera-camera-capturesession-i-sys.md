# CaptureSession

```TypeScript
interface CaptureSession
```

拍照会话类，保存一次相机运行所需要的所有资源[CameraInput](arkts-camera-camera-camerainput-i.md)、[CameraOutput](arkts-camera-camera-cameraoutput-i.md)，并向相机设备申请完成相机功能(录像，拍照)。

> **说明：** 
> 
> 从 API版本10开始支持，从API版本11开始废弃。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [VideoSession](arkts-camera-camera-videosession-i.md)

<!--Device-camera-interface CaptureSession--><!--Device-camera-interface CaptureSession-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getBeauty

```TypeScript
getBeauty(type: BeautyType): number
```

获取当前使用的美颜类型等级。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [getBeauty](arkts-camera-camera-beauty-i-sys.md#getbeauty)

<!--Device-CaptureSession-getBeauty(type: BeautyType): number--><!--Device-CaptureSession-getBeauty(type: BeautyType): number-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [BeautyType](arkts-camera-camera-beautytype-e-sys.md) | 是 | 美颜类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前使用的美颜效果等级。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

<!--Del-->
**示例**

```TypeScript
function getBeauty(captureSession: camera.CaptureSession): number {
  const invalidValue: number = -1;
  let beautyTypes: Array<camera.BeautyType> = captureSession.getSupportedBeautyTypes();
  if (beautyTypes === undefined || beautyTypes.length <= 0) {
    return invalidValue;
  }
  let beautyLevels: Array<number> = captureSession.getSupportedBeautyRange(beautyTypes[0]);
  if (beautyLevels === undefined || beautyLevels.length <= 0) {
    return invalidValue;
  }
  captureSession.setBeauty(beautyTypes[0], beautyLevels[0]);
  let beautyLevel: number = captureSession.getBeauty(beautyTypes[0]);
  return beautyLevel;
}
```

<!--DelEnd-->

## getSupportedBeautyRange

```TypeScript
getSupportedBeautyRange(type: BeautyType): Array<number>
```

获取某个美颜类型可设置的等级。不同设备支持的美颜等级不同，下表仅为示例。

| 输入参数 | 示例返回值 | 返回值描述 |  
| ----------------| ---- | ---------|  
| AUTO | [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10] | **type** 为 **AUTO** 时支持的美颜等级。值 **0** 表示关闭美颜模式，其他正整数值表示对应的自动美颜等级。 |  
| SKIN_SMOOTH | [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10] | **type** 为 **SKIN_SMOOTH** 时支持的美颜等级。值 **0** 表示关闭磨皮功能，其他正整数值表示对应的磨皮等级。 |  
| FACE_SLENDER | [0, 1, 2, 3, 4, 5] | **type** 为 **FACE_SLENDER** 时支持的美颜等级。值 **0** 表示关闭瘦脸功能，其他正整数值表示对应的瘦脸等级。 |  
| SKIN_TONE | [-1, 16242611] | **type** 为 **SKIN_TONE** 时支持的美颜等级。值 **-1** 表示关闭肤色美化功能。其他非负值表示以 RGB 表示的肤色美化等级，<br>例如 16242611，其十六进制为 0xF7D7B3，其中 F7、D7、B3 分别表示 R 通道、G 通道、B 通道的值。 |

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [getSupportedBeautyRange](arkts-camera-camera-beautyquery-i-sys.md#getsupportedbeautyrange)

<!--Device-CaptureSession-getSupportedBeautyRange(type: BeautyType): Array<number>--><!--Device-CaptureSession-getSupportedBeautyRange(type: BeautyType): Array<number>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [BeautyType](arkts-camera-camera-beautytype-e-sys.md) | 是 | 美颜类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;number&gt; | 支持的等级数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

<!--Del-->
**示例**

```TypeScript
function getSupportedBeautyRange(captureSession: camera.CaptureSession): Array<number> {
  let beautyTypes: Array<camera.BeautyType> = captureSession.getSupportedBeautyTypes();
  if (beautyTypes === undefined || beautyTypes.length <= 0) {
    return [];
  }
  let beautyLevels: Array<number> = captureSession.getSupportedBeautyRange(beautyTypes[0]);
  return beautyLevels;
}
```

<!--DelEnd-->

## getSupportedBeautyTypes

```TypeScript
getSupportedBeautyTypes(): Array<BeautyType>
```

获取支持的美颜类型。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [getSupportedBeautyTypes](arkts-camera-camera-beautyquery-i-sys.md#getsupportedbeautytypes)

<!--Device-CaptureSession-getSupportedBeautyTypes(): Array<BeautyType>--><!--Device-CaptureSession-getSupportedBeautyTypes(): Array<BeautyType>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[BeautyType](arkts-camera-camera-beautytype-e-sys.md)&gt; | 支持的美颜类型数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

<!--Del-->
**示例**

```TypeScript
function getSupportedBeautyTypes(captureSession: camera.CaptureSession): Array<camera.BeautyType> {
  let beautyTypes: Array<camera.BeautyType> = captureSession.getSupportedBeautyTypes();
  return beautyTypes;
}
```

<!--DelEnd-->

## setBeauty

```TypeScript
setBeauty(type: BeautyType, value: number): void
```

设置美颜类型及其等级。只有当通过[getSupportedBeautyTypes](#getsupportedbeautytypes) 获取的所有[美颜类型](arkts-camera-camera-beautytype-e-sys.md) 均被关闭时，美颜模式才会关闭。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [setBeauty](arkts-camera-camera-beauty-i-sys.md#setbeauty)

<!--Device-CaptureSession-setBeauty(type: BeautyType, value: number): void--><!--Device-CaptureSession-setBeauty(type: BeautyType, value: number): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [BeautyType](arkts-camera-camera-beautytype-e-sys.md) | 是 | 美颜类型。 |
| value | number | 是 | 美颜等级，通过[getSupportedBeautyRange](#getsupportedbeautyrange) 获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

<!--Del-->
**示例**

```TypeScript
function setBeauty(captureSession: camera.CaptureSession): void {
  let beautyTypes: Array<camera.BeautyType> = captureSession.getSupportedBeautyTypes();
  if (beautyTypes === undefined || beautyTypes.length <= 0) {
    return;
  }
  let beautyLevels: Array<number> = captureSession.getSupportedBeautyRange(beautyTypes[0]);
  if (beautyLevels === undefined || beautyLevels.length <= 0) {
    return;
  }
  captureSession.setBeauty(beautyTypes[0], beautyLevels[0]);
}
```

<!--DelEnd-->
