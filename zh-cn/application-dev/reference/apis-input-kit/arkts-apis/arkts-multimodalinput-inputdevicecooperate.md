# @ohos.multimodalInput.inputDeviceCooperate

键鼠穿越功能模块，提供两台或多台设备组网协同后键鼠共享能力，实现键鼠输入设备的跨设备协同操作。

> **说明**
>
> - 本模块接口从API Version 10开始不再维护，从API version 23开始废弃，推荐使用新接口[@ohos.cooperate](../../apis-distributed-service-kit/arkts-apis/arkts-cooperate.md) (键鼠穿越)。
>
> - 本模块接口均为系统接口。

**起始版本：** 9

**废弃版本：** 23

**替代接口：** cooperate/cooperate

**系统能力：** SystemCapability.MultimodalInput.Input.Cooperator

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [enable](arkts-input-enable-f-sys.md#enable-1) | 开启、关闭键鼠穿越，使用callback异步回调。@link @ohos.cooperate:cooperate.prepareCooperate(callback: AsyncCallback&lt;void&gt;)}、&gt; [cooperate.unprepareCooperate](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-unpreparecooperate-f-sys.md#unpreparecooperate-1)&gt; 替代。 |
| [enable](arkts-input-enable-f-sys.md#enable-2) | 开启、关闭键鼠穿越，使用Promise异步回调。@link @ohos.cooperate:cooperate.prepareCooperate()}、&gt; [cooperate.unprepareCooperate](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-unpreparecooperate-f-sys.md#unpreparecooperate-2)替代。 |
| [getState](arkts-input-getstate-f-sys.md#getstate-1) | 获取键鼠穿越开关的状态，使用callback异步回调。@link @ohos.cooperate:cooperate.getCooperateSwitchState(networkId: string, callback: AsyncCallback&lt;boolean&gt;)}&gt; 替代。 |
| [getState](arkts-input-getstate-f-sys.md#getstate-2) | 获取键鼠穿越开关的状态，使用Promise异步回调。@link @ohos.cooperate:cooperate.getCooperateSwitchState(networkId: string)}替&gt; 代。 |
| [off](arkts-input-off-f-sys.md#off-1) | 关闭监听键鼠穿越状态，使用callback异步回调。@link @ohos.cooperate:cooperate.off(type: 'cooperateMessage', callback?: Callback&lt;CooperateMessage&gt;)}&gt; 替代。 |
| [on](arkts-input-on-f-sys.md#on-1) | 注册监听键鼠穿越状态，使用callback异步回调。@link @ohos.cooperate:cooperate.on(type: 'cooperateMessage', callback: Callback&lt;CooperateMessage&gt;)}&gt; 替代。 |
| [start](arkts-input-start-f-sys.md#start-1) | 启动键鼠穿越，使用callback异步回调。@link @ohos.cooperate:cooperate.activateCooperate(targetNetworkId: string, inputDeviceId: int, callback: AsyncCallback&lt;void&gt;)}&gt; 替代。 |
| [start](arkts-input-start-f-sys.md#start-2) | 启动键鼠穿越，使用Promise异步回调。@link @ohos.cooperate:cooperate.activateCooperate(targetNetworkId: string, inputDeviceId: int)}&gt; 替代。 |
| [stop](arkts-input-stop-f-sys.md#stop-1) | 停止键鼠穿越，使用callback异步回调。@link @ohos.cooperate:cooperate.deactivateCooperate(isUnchained: boolean, callback: AsyncCallback&lt;void&gt;)}&gt; 替代。 |
| [stop](arkts-input-stop-f-sys.md#stop-2) | 停止键鼠穿越，使用Promise异步回调。@link @ohos.cooperate:cooperate.deactivateCooperate(isUnchained: boolean)}替代。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [EventMsg](arkts-input-eventmsg-e-sys.md) | 键鼠穿越事件。@link @ohos.cooperate:cooperate.CooperateMessage}替&gt; 代。 |
<!--DelEnd-->

