# unbind

## unbind

```TypeScript
function unbind(floatViewController: FloatViewController,
    floatingBallController: floatingBall.FloatingBallController): Promise<void>
```

解绑标准悬浮窗和闪控球。需要在[标准悬浮窗控制器](arkts-arkui-floatview-floatviewcontroller-i.md#FloatViewController)和
[闪控球控制器](arkts-arkui-floatingball-floatingballcontroller-i.md#FloatingBallController)均停止后才可解绑。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| floatViewController | FloatViewController | 是 | 标准悬浮窗控制器。 |
| floatingBallController | floatingBall.FloatingBallController | 是 | 闪控球控制器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported on this device. Possible cause:<br/>Call api on unsupported device. |
| [1300025](../../errorcode-universal.md#1300025-The) | The floating ball state does not support this operation. Possible cause:<br/>1. The floating ball has started but not stopped yet.<br/>2. The floatingBallController has not been bound. |
| [1300031](../../errorcode-universal.md#1300031-The) | The floatView state does not support this operation. Possible cause:<br/>1. The float view has started but not stopped yet.<br/>2. The floatViewController has not been bound.<br/>3. The floatViewController and the floatingBallController are not bound together. |

**示例：**

```TypeScript
// Entry.ets
import { BusinessError } from '@kit.BasicServicesKit';
import { floatingBall } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  private floatingBallController: floatingBall.FloatingBallController | undefined = undefined;
  private floatViewController: floatView.FloatViewController | undefined = undefined;
  // 创建控制器
  // ...
  public unbindController(): void {
    try {
      // 使用绑定时传入的闪控窗和闪控球控制器
      if (this.floatViewController && this.floatingBallController) {
        floatView.unbind(this.floatViewController!, this.floatingBallController!).then(() => {
          console.info('Succeeded in unbinding float view and floating ball.');
        }).catch((err: BusinessError): void => {
          console.error(`Failed to unbind float view and floating ball. Cause:${err.code}, message:${err.message}`);
        });
      }
    } catch(e) {
      console.error(`Failed to unbind float view and floating ball. Cause:${e.code}, message:${e.message}`);
    }
  }
}

```

