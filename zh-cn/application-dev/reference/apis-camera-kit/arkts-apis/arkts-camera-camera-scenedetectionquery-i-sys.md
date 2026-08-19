# SceneDetectionQuery（系统接口）

Provides the scene detection and query capabilities.

**起始版本：** 23

<!--Device-camera-interface SceneDetectionQuery--><!--Device-camera-interface SceneDetectionQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## isSceneFeatureSupported

```TypeScript
isSceneFeatureSupported(type: SceneFeatureType): boolean
```

Checks whether a scene feature is supported.

**起始版本：** 23

<!--Device-SceneDetectionQuery-isSceneFeatureSupported(type: SceneFeatureType): boolean--><!--Device-SceneDetectionQuery-isSceneFeatureSupported(type: SceneFeatureType): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [SceneFeatureType](arkts-camera-camera-scenefeaturetype-e-sys.md) | 是 | Scene feature. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Check result for the support of the scene feature. **true** if supported, **false** otherwise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application, only throw in session usage. |

**示例**

```TypeScript
function isSceneFeatureSupported(photoSessionForSys: camera.PhotoSessionForSys, featureType: camera.SceneFeatureType): boolean {
  let isSupported: boolean = photoSessionForSys.isSceneFeatureSupported(featureType);
  return isSupported;
}
```

