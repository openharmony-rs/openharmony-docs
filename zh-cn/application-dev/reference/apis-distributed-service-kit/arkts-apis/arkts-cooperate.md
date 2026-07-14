# @ohos.cooperate

键鼠穿越功能模块，提供两台或多台设备组网协同后键鼠共享能力，实现键鼠输入设备的跨设备协同操作。

> **说明**
>
> - 本模块接口均为系统接口。

**起始版本：** 10

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [activate](arkts-distributedservice-activate-f-sys.md#activate-1) | 启动键鼠穿越，使用Callback异步回调。 |
| [activate](arkts-distributedservice-activate-f-sys.md#activate-2) | 启动键鼠穿越，使用Promise异步回调。 |
| [activateCooperate](arkts-distributedservice-activatecooperate-f-sys.md#activatecooperate-1) | 启动键鼠穿越，使用Callback异步回调。 |
| [activateCooperate](arkts-distributedservice-activatecooperate-f-sys.md#activatecooperate-2) | 启动键鼠穿越，使用Promise异步回调。 |
| [activateCooperateWithOptions](arkts-distributedservice-activatecooperatewithoptions-f-sys.md#activatecooperatewithoptions-1) | 启动键鼠穿越，使用选项开始屏幕跳转。 |
| [deactivate](arkts-distributedservice-deactivate-f-sys.md#deactivate-1) | 停止键鼠穿越，使用Callback异步回调。 |
| [deactivate](arkts-distributedservice-deactivate-f-sys.md#deactivate-2) | 停止键鼠穿越，使用Promise异步回调。 |
| [deactivateCooperate](arkts-distributedservice-deactivatecooperate-f-sys.md#deactivatecooperate-1) | 停止键鼠穿越，使用Callback异步回调。 |
| [deactivateCooperate](arkts-distributedservice-deactivatecooperate-f-sys.md#deactivatecooperate-2) | 停止键鼠穿越，使用Promise异步回调。 |
| [getCooperateSwitchState](arkts-distributedservice-getcooperateswitchstate-f-sys.md#getcooperateswitchstate-1) | 获取目标设备键鼠穿越开关的状态，使用Callback异步回调。 |
| [getCooperateSwitchState](arkts-distributedservice-getcooperateswitchstate-f-sys.md#getcooperateswitchstate-2) | 获取目标设备键鼠穿越开关的状态，使用Promise异步方式返回结果。 |
| [getCrossingSwitchState](arkts-distributedservice-getcrossingswitchstate-f-sys.md#getcrossingswitchstate-1) | 获取目标设备键鼠穿越开关的状态，使用Callback异步回调。 |
| [getCrossingSwitchState](arkts-distributedservice-getcrossingswitchstate-f-sys.md#getcrossingswitchstate-2) | 获取目标设备键鼠穿越开关的状态，使用Promise异步方式返回结果。 |
| [off](arkts-distributedservice-off-f-sys.md#off-1) | 取消监听键鼠穿越状态。 |
| [off](arkts-distributedservice-off-f-sys.md#off-2) | 取消监听键鼠穿越状态。 |
| [off](arkts-distributedservice-off-f-sys.md#off-3) | 取消监听指定设备鼠标光标位置。 |
| [on](arkts-distributedservice-on-f-sys.md#on-1) | 注册监听键鼠穿越状态。 |
| [on](arkts-distributedservice-on-f-sys.md#on-2) | 注册监听键鼠穿越状态。 |
| [on](arkts-distributedservice-on-f-sys.md#on-3) | 注册监听指定设备鼠标光标位置。 |
| [prepare](arkts-distributedservice-prepare-f-sys.md#prepare-1) | 准备键鼠穿越，使用Callback异步回调。 |
| [prepare](arkts-distributedservice-prepare-f-sys.md#prepare-2) | 准备键鼠穿越，使用Promise异步方式返回结果。 |
| [prepareCooperate](arkts-distributedservice-preparecooperate-f-sys.md#preparecooperate-1) | 准备键鼠穿越，使用Callback异步回调。 |
| [prepareCooperate](arkts-distributedservice-preparecooperate-f-sys.md#preparecooperate-2) | 准备键鼠穿越，使用Promise异步方式返回结果。 |
| [unprepare](arkts-distributedservice-unprepare-f-sys.md#unprepare-1) | 取消键鼠穿越准备，使用Callback异步回调。 |
| [unprepare](arkts-distributedservice-unprepare-f-sys.md#unprepare-2) | 取消键鼠穿越准备，使用Promise异步回调。 |
| [unprepareCooperate](arkts-distributedservice-unpreparecooperate-f-sys.md#unpreparecooperate-1) | 取消键鼠穿越准备，使用Callback异步回调。 |
| [unprepareCooperate](arkts-distributedservice-unpreparecooperate-f-sys.md#unpreparecooperate-2) | 取消键鼠穿越准备，使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CooperateMessage](arkts-distributedservice-cooperatemessage-i-sys.md) | 键鼠穿越的消息。 |
| [CooperateOptions](arkts-distributedservice-cooperateoptions-i-sys.md) | 键鼠穿越可选控制参数，控制穿出点位置。 |
| [MouseLocation](arkts-distributedservice-mouselocation-i-sys.md) | 键鼠穿越的位置。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CooperateMsg](arkts-distributedservice-cooperatemsg-e-sys.md) | 键鼠穿越的消息通知。 |
| [CooperateState](arkts-distributedservice-cooperatestate-e-sys.md) | 键鼠穿越状态的枚举。 |
<!--DelEnd-->

