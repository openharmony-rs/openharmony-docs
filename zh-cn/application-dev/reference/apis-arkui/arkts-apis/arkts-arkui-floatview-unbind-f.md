# unbind

## unbind

```TypeScript
function unbind(floatViewController: FloatViewController,
    floatingBallController: floatingBall.FloatingBallController): Promise<void>
```

解绑标准悬浮窗和闪控球。需要在[标准悬浮窗控制器]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_和 [闪控球控制器]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_均停止后才可解绑。使用Promise异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-floatView-function unbind(floatViewController: FloatViewController,    floatingBallController: floatingBall.FloatingBallController): Promise<void>--><!--Device-floatView-function unbind(floatViewController: FloatViewController,    floatingBallController: floatingBall.FloatingBallController): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| floatViewController | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 标准悬浮窗控制器。 |
| floatingBallController | floatingBall.FloatingBallController | 是 | 闪控球控制器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported on this device. Possible cause:Call api on unsupported device. |
| [1300025](../errorcode-window.md#1300025-闪控球状态不支持该操作) | The floating ball state does not support this operation. Possible cause:1. The floating ball has started but not stopped yet.2. The floatingBallController has not been bound. |
| [1300031](../errorcode-window.md#1300031-闪控窗状态不支持该操作) | The floatView state does not support this operation. Possible cause:1. The float view has started but not stopped yet.2. The floatViewController has not been bound.3. The floatViewController and the floatingBallController are not bound together. |

