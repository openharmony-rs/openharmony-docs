# DepthFusion（系统接口）

Depth fusion class. It inherits from [DepthFusionQuery]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_.

**继承/实现关系：** DepthFusion extends [DepthFusionQuery](arkts-camera-camera-depthfusionquery-i-sys.md)

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

<!--Device-camera-interface DepthFusion extends DepthFusionQuery--><!--Device-camera-interface DepthFusion extends DepthFusionQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## enableDepthFusion

```TypeScript
enableDepthFusion(enabled: boolean): void
```

Enables depth fusion.

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

<!--Device-DepthFusion-enableDepthFusion(enabled: boolean): void--><!--Device-DepthFusion-enableDepthFusion(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | Whether to enable depth fusion. **true** to enable, **false** otherwise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例：**

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

## isDepthFusionEnabled

```TypeScript
isDepthFusionEnabled(): boolean
```

Checks whether depth fusion is enabled.

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

<!--Device-DepthFusion-isDepthFusionEnabled(): boolean--><!--Device-DepthFusion-isDepthFusionEnabled(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Check result for whether depth fusion is enabled. **true** if enabled, **false** otherwise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

**示例：**

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

