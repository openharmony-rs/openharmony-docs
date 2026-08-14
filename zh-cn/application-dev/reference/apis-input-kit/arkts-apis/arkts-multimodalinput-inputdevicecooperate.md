# @ohos.multimodalInput.inputDeviceCooperate

键鼠穿越功能模块，提供两台或多台设备组网协同后键鼠共享能力，实现键鼠输入设备的跨设备协同操作。 > **说明：**> > - 本模块接口从API Version 10开始不再维护，从API version 23开始废弃，推荐使用新接口[@ohos.cooperate](../../apis-distributed-service-kit/arkts-apis/arkts-cooperate.md#@ohos.cooperate) (键鼠穿越)。 > > - 本模块接口均为系统接口。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 23

**替代接口：** [cooperate/cooperate](../../apis-distributed-service-kit/arkts-apis/arkts-cooperate.md#@ohos.cooperate)

<!--Device-unnamed-declare namespace inputDeviceCooperate--><!--Device-unnamed-declare namespace inputDeviceCooperate-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Cooperator

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [enable](arkts-input-inputdevicecooperate-enable-f-sys.md#enable) | 开启、关闭键鼠穿越，使用callback异步回调。 |
| [enable](arkts-input-inputdevicecooperate-enable-f-sys.md#enable（系统接口）) | 开启、关闭键鼠穿越，使用Promise异步回调。 |
| [getState](arkts-input-inputdevicecooperate-getstate-f-sys.md#getState) | 获取键鼠穿越开关的状态，使用callback异步回调。 |
| [getState](arkts-input-inputdevicecooperate-getstate-f-sys.md#getState（系统接口）) | 获取键鼠穿越开关的状态，使用Promise异步回调。 |
| [off_cooperation](arkts-input-inputdevicecooperate-offcooperation-f-sys.md#off_cooperation) | 关闭监听键鼠穿越状态，使用callback异步回调。 |
| [on_cooperation](arkts-input-inputdevicecooperate-oncooperation-f-sys.md#on_cooperation) | 注册监听键鼠穿越状态，使用callback异步回调。 |
| [start](arkts-input-inputdevicecooperate-start-f-sys.md#start) | 启动键鼠穿越，使用callback异步回调。 |
| [start](arkts-input-inputdevicecooperate-start-f-sys.md#start（系统接口）) | 启动键鼠穿越，使用Promise异步回调。 |
| [stop](arkts-input-inputdevicecooperate-stop-f-sys.md#stop) | 停止键鼠穿越，使用callback异步回调。 |
| [stop](arkts-input-inputdevicecooperate-stop-f-sys.md#stop（系统接口）) | 停止键鼠穿越，使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [EventMsg](arkts-input-inputdevicecooperate-eventmsg-e-sys.md) | 键鼠穿越事件。 |
<!--DelEnd-->

