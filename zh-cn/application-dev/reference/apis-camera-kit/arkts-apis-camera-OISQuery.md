# Interface (OISQuery)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leoqsl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

光学防抖（OIS）查询对象。

> **说明：**
>
> - 本模块首批接口从API version 10 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本Interface首批接口从API version 24开始支持。

## 导入模块

```ts
import { camera } from '@kit.CameraKit';
```

## isOISModeSupported<sup>24+</sup>

isOISModeSupported(mode: OISMode): boolean

检测是否支持指定的OIS模式。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名     | 类型             | 必填 | 说明       |
| -------- | --------------- | ---- | --------- |
| mode | [OISMode](arkts-apis-camera-e.md#oismode24) | 是 | 设置的OIS模式。 |

**返回值：**

| 类型        | 说明                          |
| ---------- | ----------------------------- |
| boolean    | 当前设备是否支持指定的OIS模式。返回true表示支持指，返回false表示不支持。 |

**错误码：**

以下错误码的详细介绍请参见[Camera错误码](errorcode-camera.md)。

| 错误码ID         | 错误信息        |
| --------------- | --------------- |
| 7400102 | Operation not allowed, the inputDevice or the session is abnormal. |
| 7400103 | Session not config. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function isOISModeSupported(photoSession: camera.PhotoSession, mode: camera.OISMode): boolean {
  let isSupported = false;
  try {
    isSupported = photoSession.isOISModeSupported(mode);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The isOISModeSupported call failed. error code: ${err.code}`);
  }
  return isSupported;
}
```

## getSupportedOISBiasRange<sup>24+</sup>

getSupportedOISBiasRange(oisAxis: OISAxes): Array\<number\>

获取指定OIS轴向支持的偏置范围。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名     | 类型             | 必填 | 说明       |
| -------- | --------------- | ---- | --------- |
| oisAxis | [OISAxes](arkts-apis-camera-e.md#oisaxes24) | 是 | OIS轴向。 |

**返回值：**

| 类型        | 说明                          |
| ---------- | ----------------------------- |
| Array\<number\>    | 偏置范围。 |

**错误码：**

以下错误码的详细介绍请参见[Camera错误码](errorcode-camera.md)。

| 错误码ID         | 错误信息        |
| --------------- | --------------- |
| 7400102 | Operation not allowed, the inputDevice or the session is abnormal. |
| 7400103 | Session not config. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getSupportedOISBiasRange(photoSession: camera.PhotoSession, oisAxis: camera.OISAxes): Array<number> {
  let biasRange: Array<number> = [];
  try {
    biasRange = photoSession.getSupportedOISBiasRange(oisAxis);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The getSupportedOISBiasRange call failed. error code: ${err.code}`);
  }
  return biasRange;
}
```

## getSupportedOISBiasStep<sup>24+</sup>

getSupportedOISBiasStep(oisAxis: OISAxes): number

获取指定OIS轴向的偏置步长。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名     | 类型             | 必填 | 说明       |
| -------- | --------------- | ---- | --------- |
| oisAxis | [OISAxes](arkts-apis-camera-e.md#oisaxes24) | 是 | OIS轴向。 |

**返回值：**

| 类型        | 说明                          |
| ---------- | ----------------------------- |
| number    | 偏置步长值。 |

**错误码：**

以下错误码的详细介绍请参见[Camera错误码](errorcode-camera.md)。

| 错误码ID         | 错误信息        |
| --------------- | --------------- |
| 7400102 | Operation not allowed, the inputDevice or the session is abnormal. |
| 7400103 | Session not config. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getSupportedOISBiasStep(photoSession: camera.PhotoSession, oisAxis: camera.OISAxes): number {
  let biasStep = 0.0;
  try {
    biasStep = photoSession.getSupportedOISBiasStep(oisAxis);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The getSupportedOISBiasStep call failed. error code: ${err.code}`);
  }
  return biasStep;
}
```

## getCurrentOISMode<sup>24+</sup>

getCurrentOISMode(): OISMode

获取当前OIS模式。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型        | 说明                          |
| ---------- | ----------------------------- |
| [OISMode](arkts-apis-camera-e.md#oismode24)    | 当前OIS模式。 |

**错误码：**

以下错误码的详细介绍请参见[Camera错误码](errorcode-camera.md)。

| 错误码ID         | 错误信息        |
| --------------- | --------------- |
| 7400102 | Operation not allowed, the inputDevice or the session is abnormal. |
| 7400103 | Session not config. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getCurrentOISMode(photoSession: camera.PhotoSession): camera.OISMode {
  let mode: camera.OISMode = camera.OISMode.OFF;
  try {
    mode = photoSession.getCurrentOISMode();
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The getCurrentOISMode call failed. error code: ${err.code}`);
  }
  return mode;
}
```

## getCurrentCustomOISBias<sup>24+</sup>

getCurrentCustomOISBias(oisAxis: OISAxes): number

获取指定OIS轴向的当前自定义偏置值。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名     | 类型             | 必填 | 说明       |
| -------- | --------------- | ---- | --------- |
| oisAxis | [OISAxes](arkts-apis-camera-e.md#oisaxes24) | 是 | OIS轴向。 |

**返回值：**

| 类型        | 说明                          |
| ---------- | ----------------------------- |
| number    | 当前偏置值。 |

**错误码：**

以下错误码的详细介绍请参见[Camera错误码](errorcode-camera.md)。

| 错误码ID         | 错误信息        |
| --------------- | --------------- |
| 7400102 | Operation not allowed, the inputDevice or the session is abnormal. |
| 7400103 | Session not config. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getCurrentCustomOISBias(photoSession: camera.PhotoSession, oisAxis: camera.OISAxes): number {
  let bias = 0.0;
  try {
    bias = photoSession.getCurrentCustomOISBias(oisAxis);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The getCurrentCustomOISBias call failed. error code: ${err.code}`);
  }
  return bias;
}
```