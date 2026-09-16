# DepthFusionQuery（系统接口）

A class for querying depth fusion capabilities.

**起始版本：** 14

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

Obtains the depth fusion threshold.

**起始版本：** 14

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;number&gt; | Depth fusion threshold. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

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

## isDepthFusionSupported

```TypeScript
isDepthFusionSupported(): boolean
```

Checks whether depth fusion is supported.

**起始版本：** 14

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Check result for the support of depth fusion. **true** if supported, **false** otherwise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

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
