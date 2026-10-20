# DepthFusion（系统接口）

```TypeScript
interface DepthFusion extends DepthFusionQuery
```

深度融合类。继承自 [DepthFusionQuery](arkts-camera-camera-depthfusionquery-i-sys.md)。

**继承/实现关系：** DepthFusion extends [DepthFusionQuery](arkts-camera-camera-depthfusionquery-i-sys.md)

**起始版本：** 14

<!--Device-camera-interface DepthFusion extends DepthFusionQuery--><!--Device-camera-interface DepthFusion extends DepthFusionQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## enableDepthFusion

```TypeScript
enableDepthFusion(enabled: boolean): void
```

启用深度融合。

**起始版本：** 14

<!--Device-DepthFusion-enableDepthFusion(enabled: boolean): void--><!--Device-DepthFusion-enableDepthFusion(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 是否启用深度融合。**true** 表示启用，**false** 表示不启用 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function enableDepthFusion(DepthFusion: camera.DepthFusion): void {
  try {
    let enabled: boolean = true;
    DepthFusion.enableDepthFusion(enabled);
    console.info('Promise returned to indicate that enableDepthFusion method execution success.');
  } catch (error) {
    let err = error as BusinessError;
    console.error(`Failed to depth fusion enableDepthFusion, error code: ${err.code}.`);
  };
}
```

<!--DelEnd-->

## isDepthFusionEnabled

```TypeScript
isDepthFusionEnabled(): boolean
```

查询是否已启用深度融合。

**起始版本：** 14

<!--Device-DepthFusion-isDepthFusionEnabled(): boolean--><!--Device-DepthFusion-isDepthFusionEnabled(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 查询是否已启用深度融合的结果。**true** 表示已启用，**false** 表示未启用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function isDepthFusionEnabled(DepthFusion: camera.DepthFusion): boolean {
  let isEnable: boolean = false;
  try {
    isEnable = DepthFusion.isDepthFusionEnabled();
    console.info('Promise returned to indicate that isDepthFusionEnabled method execution success.');
  } catch (error) {
    let err = error as BusinessError;
    console.error(`Failed to depth fusion isDepthFusionEnabled, error code: ${err.code}.`);
  };
  return isEnable;
}
```

<!--DelEnd-->
