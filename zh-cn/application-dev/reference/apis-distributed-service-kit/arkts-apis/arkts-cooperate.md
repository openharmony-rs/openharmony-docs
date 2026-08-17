# @ohos.cooperate

键鼠穿越功能模块，提供两台或多台设备组网协同后键鼠共享能力，实现键鼠输入设备的跨设备协同操作。 > **说明：**> > - 本模块接口均为系统接口。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace cooperate--><!--Device-unnamed-declare namespace cooperate-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [activate](arkts-distributedservice-cooperate-activate-f-sys.md#activate) | 启动键鼠穿越，使用Callback异步回调。 |
| [activate](arkts-distributedservice-cooperate-activate-f-sys.md#activate系统接口) | 启动键鼠穿越，使用Promise异步回调。 |
| [activateCooperate](arkts-distributedservice-cooperate-activatecooperate-f-sys.md#activatecooperate) | 启动键鼠穿越，使用Callback异步回调。 |
| [activateCooperate](arkts-distributedservice-cooperate-activatecooperate-f-sys.md#activatecooperate系统接口) | 启动键鼠穿越，使用Promise异步回调。 |
| [activateCooperateWithOptions](arkts-distributedservice-cooperate-activatecooperatewithoptions-f-sys.md#activatecooperatewithoptions) | 启动键鼠穿越，使用选项开始屏幕跳转。 |
| [deactivate](arkts-distributedservice-cooperate-deactivate-f-sys.md#deactivate) | 停止键鼠穿越，使用Callback异步回调。 |
| [deactivate](arkts-distributedservice-cooperate-deactivate-f-sys.md#deactivate系统接口) | 停止键鼠穿越，使用Promise异步回调。 |
| [deactivateCooperate](arkts-distributedservice-cooperate-deactivatecooperate-f-sys.md#deactivatecooperate) | 停止键鼠穿越，使用Callback异步回调。 |
| [deactivateCooperate](arkts-distributedservice-cooperate-deactivatecooperate-f-sys.md#deactivatecooperate系统接口) | 停止键鼠穿越，使用Promise异步回调。 |
| [getCooperateSwitchState](arkts-distributedservice-cooperate-getcooperateswitchstate-f-sys.md#getcooperateswitchstate) | 获取目标设备键鼠穿越开关的状态，使用Callback异步回调。 |
| [getCooperateSwitchState](arkts-distributedservice-cooperate-getcooperateswitchstate-f-sys.md#getcooperateswitchstate系统接口) | 获取目标设备键鼠穿越开关的状态，使用Promise异步方式返回结果。 |
| [getCrossingSwitchState](arkts-distributedservice-cooperate-getcrossingswitchstate-f-sys.md#getcrossingswitchstate) | 获取目标设备键鼠穿越开关的状态，使用Callback异步回调。 |
| [getCrossingSwitchState](arkts-distributedservice-cooperate-getcrossingswitchstate-f-sys.md#getcrossingswitchstate系统接口) | 获取目标设备键鼠穿越开关的状态，使用Promise异步方式返回结果。 |
| [offCooperateMessage](arkts-distributedservice-cooperate-offcooperatemessage-f-sys.md#offcooperatemessage) | Disables listening for screen hopping status change events. |
| [offCooperateMouseEvent](arkts-distributedservice-cooperate-offcooperatemouseevent-f-sys.md#offcooperatemouseevent) | Disables listening for mouse pointer position information on the specified device for cooperation. |
| [off_cooperate](arkts-distributedservice-cooperate-offcooperate-f-sys.md#offcooperate) | 取消监听键鼠穿越状态。 |
| [off_cooperateMessage](arkts-distributedservice-cooperate-offcooperatemessage-f-sys.md#offcooperatemessage) | 取消监听键鼠穿越状态。 |
| [off_cooperateMouse](arkts-distributedservice-cooperate-offcooperatemouse-f-sys.md#offcooperatemouse) | 取消监听指定设备鼠标光标位置。 |
| [onCooperateMessage](arkts-distributedservice-cooperate-oncooperatemessage-f-sys.md#oncooperatemessage) | Enables listening for screen hopping status change events. |
| [onCooperateMouseEvent](arkts-distributedservice-cooperate-oncooperatemouseevent-f-sys.md#oncooperatemouseevent) | Enables listening for mouse pointer position information on the specified device for cooperation. |
| [on_cooperate](arkts-distributedservice-cooperate-oncooperate-f-sys.md#oncooperate) | 注册监听键鼠穿越状态。 |
| [on_cooperateMessage](arkts-distributedservice-cooperate-oncooperatemessage-f-sys.md#oncooperatemessage) | 注册监听键鼠穿越状态。 |
| [on_cooperateMouse](arkts-distributedservice-cooperate-oncooperatemouse-f-sys.md#oncooperatemouse) | 注册监听指定设备鼠标光标位置。 |
| [prepare](arkts-distributedservice-cooperate-prepare-f-sys.md#prepare) | 准备键鼠穿越，使用Callback异步回调。 |
| [prepare](arkts-distributedservice-cooperate-prepare-f-sys.md#prepare系统接口) | 准备键鼠穿越，使用Promise异步方式返回结果。 |
| [prepareCooperate](arkts-distributedservice-cooperate-preparecooperate-f-sys.md#preparecooperate) | 准备键鼠穿越，使用Callback异步回调。 |
| [prepareCooperate](arkts-distributedservice-cooperate-preparecooperate-f-sys.md#preparecooperate系统接口) | 准备键鼠穿越，使用Promise异步方式返回结果。 |
| [unprepare](arkts-distributedservice-cooperate-unprepare-f-sys.md#unprepare) | 取消键鼠穿越准备，使用Callback异步回调。 |
| [unprepare](arkts-distributedservice-cooperate-unprepare-f-sys.md#unprepare系统接口) | 取消键鼠穿越准备，使用Promise异步回调。 |
| [unprepareCooperate](arkts-distributedservice-cooperate-unpreparecooperate-f-sys.md#unpreparecooperate) | 取消键鼠穿越准备，使用Callback异步回调。 |
| [unprepareCooperate](arkts-distributedservice-cooperate-unpreparecooperate-f-sys.md#unpreparecooperate系统接口) | 取消键鼠穿越准备，使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CooperateMessage](arkts-distributedservice-cooperate-cooperatemessage-i-sys.md) | 键鼠穿越的消息。 |
| [CooperateOptions](arkts-distributedservice-cooperate-cooperateoptions-i-sys.md) | 键鼠穿越可选控制参数，控制穿出点位置。 |
| [MouseLocation](arkts-distributedservice-cooperate-mouselocation-i-sys.md) | 键鼠穿越的位置。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CooperateMsg](arkts-distributedservice-cooperate-cooperatemsg-e-sys.md) | 键鼠穿越的消息通知。 |
| [CooperateState](arkts-distributedservice-cooperate-cooperatestate-e-sys.md) | 键鼠穿越状态的枚举。 |
<!--DelEnd-->

