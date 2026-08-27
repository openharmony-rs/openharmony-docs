# startBlinking（系统接口）

## 导入模块

```TypeScript
import { config } from '@kit.AccessibilityKit';
```

## startBlinking

```TypeScript
function startBlinking(mode: BlinkingMode, scenario: BlinkingScenario): BlinkResultCode
```

启用闪光灯或屏幕以进行闪烁提醒。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [BlinkingMode](arkts-accessibility-config-blinkingmode-e-sys.md) | 是 | 表示屏幕闪烁或闪光灯闪烁的模式。 |
| scenario | [BlinkingScenario](arkts-accessibility-config-blinkingscenario-e-sys.md) | 是 | 表示触发闪烁的场景。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BlinkResultCode](arkts-accessibility-config-blinkresultcode-e-sys.md) | 接口调用返回的结果码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [9300000](../errorcode-accessibility.md#9300000-无障碍系统服务工作异常) | System abnormality.Possible causes:  1.Internal operation failed.  2.Failed to obtain the required service or client object (null pointer).  3.IPC communication failed.  4.Failed to obtain the accessibility service proxy. |

**示例**

```TypeScript
import { config } from '@kit.AccessibilityKit';

try {
  let code: config.BlinkResultCode = config.startBlinking(config.BlinkingMode.SINGLE_BLINK, config.BlinkingScenario.ALARM);
  console.info(`Succeeded in startBlinking, result code: ${code}`);
} catch (err) {
  console.error(`Failed to call startBlinking, code is ${err.code}, message is ${err.message}`);
}
```
