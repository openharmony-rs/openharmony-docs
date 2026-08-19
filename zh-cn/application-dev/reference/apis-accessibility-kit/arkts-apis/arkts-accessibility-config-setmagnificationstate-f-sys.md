# setMagnificationState（系统接口）

## 导入模块

```TypeScript
import { config } from '@kit.AccessibilityKit';
```

## setMagnificationState

```TypeScript
function setMagnificationState(state: boolean): void
```

设置放大效果的启用状态。放大效果依赖放大手势功能，仅在放大手势功能已启用的前提下，本接口的设置才会生效。

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_ACCESSIBILITY_CONFIG

<!--Device-config-function setMagnificationState(state: boolean): void--><!--Device-config-function setMagnificationState(state: boolean): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | boolean | 是 | 表示放大效果的启用状态。 <br>- true：表示启用放大效果。 <br>- false：表示关闭放大效果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [9300007](../errorcode-accessibility.md#9300007-触发放大功能失败) | Trigger magnification failed. |

**示例**

```TypeScript
import { config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  config.setMagnificationState(true);
} catch (err) {
  let e = err as BusinessError;
  console.error(`Failed to set magnification. Code: ${e.code}, message: ${e.message}`);
}
```

