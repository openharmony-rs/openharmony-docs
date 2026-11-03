# SceneDetectionQuery（系统接口）

```TypeScript
interface SceneDetectionQuery
```

提供场景检测与查询能力。

**起始版本：** 12

<!--Device-camera-interface SceneDetectionQuery--><!--Device-camera-interface SceneDetectionQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## isSceneFeatureSupported

```TypeScript
isSceneFeatureSupported(type: SceneFeatureType): boolean
```

检查是否支持指定的场景特性。

**起始版本：** 12

<!--Device-SceneDetectionQuery-isSceneFeatureSupported(type: SceneFeatureType): boolean--><!--Device-SceneDetectionQuery-isSceneFeatureSupported(type: SceneFeatureType): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [SceneFeatureType](arkts-camera-camera-scenefeaturetype-e-sys.md) | 是 | 场景特性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否支持该场景特性。**true**表示支持，**false**表示不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application, only throw in session usage. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |

<!--Del-->
**示例**

```TypeScript
function isSceneFeatureSupported(photoSessionForSys: camera.PhotoSessionForSys, featureType: camera.SceneFeatureType): boolean {
  let isSupported: boolean = photoSessionForSys.isSceneFeatureSupported(featureType);
  return isSupported;
}
```

<!--DelEnd-->
