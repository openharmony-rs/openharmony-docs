# @ohos.cooperate

键鼠穿越功能模块，提供两台或多台设备组网协同后键鼠共享能力，实现键鼠输入设备的跨设备协同操作。
> **说明**  
>  
> - 本模块接口均为系统接口。

**起始版本：** 10

<!--Device-unnamed-declare namespace cooperate--><!--Device-unnamed-declare namespace cooperate-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cooperate } from '@kit.DistributedServiceKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [activate](arkts-distributedservice-cooperate-activate-f-sys.md#activate) | 启动键鼠穿越，使用Callback异步回调。 |
| [activate](arkts-distributedservice-cooperate-activate-f-sys.md#activate-1) | 启动键鼠穿越，使用Promise异步回调。 |
| [activateCooperate](arkts-distributedservice-cooperate-activatecooperate-f-sys.md#activatecooperate) | 启动键鼠穿越，使用Callback异步回调。 |
| [activateCooperate](arkts-distributedservice-cooperate-activatecooperate-f-sys.md#activatecooperate-1) | 启动键鼠穿越，使用Promise异步回调。 |
| [activateCooperateWithOptions](arkts-distributedservice-cooperate-activatecooperatewithoptions-f-sys.md#activatecooperatewithoptions) | 启动键鼠穿越，使用选项开始屏幕跳转。 |
| [deactivate](arkts-distributedservice-cooperate-deactivate-f-sys.md#deactivate) | 停止键鼠穿越，使用Callback异步回调。 |
| [deactivate](arkts-distributedservice-cooperate-deactivate-f-sys.md#deactivate-1) | 停止键鼠穿越，使用Promise异步回调。 |
| [deactivateCooperate](arkts-distributedservice-cooperate-deactivatecooperate-f-sys.md#deactivatecooperate) | 停止键鼠穿越，使用Callback异步回调。 |
| [deactivateCooperate](arkts-distributedservice-cooperate-deactivatecooperate-f-sys.md#deactivatecooperate-1) | 停止键鼠穿越，使用Promise异步回调。 |
| [getCooperateSwitchState](arkts-distributedservice-cooperate-getcooperateswitchstate-f-sys.md#getcooperateswitchstate) | 获取目标设备键鼠穿越开关的状态，使用Callback异步回调。 |
| [getCooperateSwitchState](arkts-distributedservice-cooperate-getcooperateswitchstate-f-sys.md#getcooperateswitchstate-1) | 获取目标设备键鼠穿越开关的状态，使用Promise异步方式返回结果。 |
| [getCrossingSwitchState](arkts-distributedservice-cooperate-getcrossingswitchstate-f-sys.md#getcrossingswitchstate) | 获取目标设备键鼠穿越开关的状态，使用Callback异步回调。 |
| [getCrossingSwitchState](arkts-distributedservice-cooperate-getcrossingswitchstate-f-sys.md#getcrossingswitchstate-1) | 获取目标设备键鼠穿越开关的状态，使用Promise异步方式返回结果。 |
| [off](arkts-distributedservice-cooperate-off-f-sys.md#off) | 取消监听键鼠穿越状态。 |
| [off](arkts-distributedservice-cooperate-off-f-sys.md#off-1) | 取消监听键鼠穿越状态。 |
| [off](arkts-distributedservice-cooperate-off-f-sys.md#off-2) | 取消监听指定设备鼠标光标位置。 |
| [on](arkts-distributedservice-cooperate-on-f-sys.md#on) | 注册监听键鼠穿越状态。 |
| [on](arkts-distributedservice-cooperate-on-f-sys.md#on-1) | 注册监听键鼠穿越状态。 |
| [on](arkts-distributedservice-cooperate-on-f-sys.md#on-2) | 注册监听指定设备鼠标光标位置。 |
| [prepare](arkts-distributedservice-cooperate-prepare-f-sys.md#prepare) | 准备键鼠穿越，使用Callback异步回调。 |
| [prepare](arkts-distributedservice-cooperate-prepare-f-sys.md#prepare-1) | 准备键鼠穿越，使用Promise异步方式返回结果。 |
| [prepareCooperate](arkts-distributedservice-cooperate-preparecooperate-f-sys.md#preparecooperate) | 准备键鼠穿越，使用Callback异步回调。 |
| [prepareCooperate](arkts-distributedservice-cooperate-preparecooperate-f-sys.md#preparecooperate-1) | 准备键鼠穿越，使用Promise异步方式返回结果。 |
| [unprepare](arkts-distributedservice-cooperate-unprepare-f-sys.md#unprepare) | 取消键鼠穿越准备，使用Callback异步回调。 |
| [unprepare](arkts-distributedservice-cooperate-unprepare-f-sys.md#unprepare-1) | 取消键鼠穿越准备，使用Promise异步回调。 |
| [unprepareCooperate](arkts-distributedservice-cooperate-unpreparecooperate-f-sys.md#unpreparecooperate) | 取消键鼠穿越准备，使用Callback异步回调。 |
| [unprepareCooperate](arkts-distributedservice-cooperate-unpreparecooperate-f-sys.md#unpreparecooperate-1) | 取消键鼠穿越准备，使用Promise异步回调。 |
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

