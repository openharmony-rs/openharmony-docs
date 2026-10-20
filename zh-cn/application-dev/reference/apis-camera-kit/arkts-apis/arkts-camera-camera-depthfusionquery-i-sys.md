# DepthFusionQuery（系统接口）

```TypeScript
interface DepthFusionQuery
```

用于查询深度融合能力的类。

**起始版本：** 14

<!--Device-camera-interface DepthFusionQuery--><!--Device-camera-interface DepthFusionQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getDepthFusionThreshold

```TypeScript
getDepthFusionThreshold(): Array<number>
```

获取深度融合阈值。

**起始版本：** 14

<!--Device-DepthFusionQuery-getDepthFusionThreshold(): Array<double>--><!--Device-DepthFusionQuery-getDepthFusionThreshold(): Array<double>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;number&gt; | 深度融合阈值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getDepthFusionThreshold(DepthFusionQuery: camera.DepthFusionQuery): void {
  try {
    let threshold: Array<number> = DepthFusionQuery.getDepthFusionThreshold();
    console.info('Promise returned to indicate that getDepthFusionThreshold method execution success.');
  } catch (error) {
    let err = error as BusinessError;
    console.error(`Failed to depth fusion query  getDepthFusionThreshold, error code: ${err.code}.`);
  }
}
```

<!--DelEnd-->

## isDepthFusionSupported

```TypeScript
isDepthFusionSupported(): boolean
```

查询是否支持深度融合。

**起始版本：** 14

<!--Device-DepthFusionQuery-isDepthFusionSupported(): boolean--><!--Device-DepthFusionQuery-isDepthFusionSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 查询是否支持深度融合的结果。**true** 表示支持，**false** 表示不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function isDepthFusionSupported(DepthFusionQuery: camera.DepthFusionQuery): void {
  try {
    let isSupported: boolean = DepthFusionQuery.isDepthFusionSupported();
    console.info('Indicate that isDepthFusionSupported method execution success.');
  } catch (error) {
    let err = error as BusinessError;
    console.error(`Failed to depth fusion query  isDepthFusionSupported, error code: ${err.code}.`);
  }
}
```

<!--DelEnd-->
