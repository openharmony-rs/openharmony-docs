# @ohos.multimodalInput.inputDeviceCooperate

键鼠穿越功能模块，提供两台或多台设备组网协同后键鼠共享能力，实现键鼠输入设备的跨设备协同操作。

**起始版本：** 9

**废弃版本：** 23

**替代接口：** [cooperate/cooperate](../../apis-distributed-service-kit/arkts-apis/arkts-cooperate.md)

<!--Device-unnamed-declare namespace inputDeviceCooperate--><!--Device-unnamed-declare namespace inputDeviceCooperate-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Cooperator

## 导入模块

```TypeScript
import { inputDeviceCooperate } from '@kit.InputKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [enable](arkts-input-inputdevicecooperate-enable-f-sys.md) | 开启、关闭键鼠穿越，使用callback异步回调。 |
| [enable](arkts-input-inputdevicecooperate-enable-f-sys.md) | 开启、关闭键鼠穿越，使用Promise异步回调。 |
| [getState](arkts-input-inputdevicecooperate-getstate-f-sys.md) | 获取键鼠穿越开关的状态，使用callback异步回调。 |
| [getState](arkts-input-inputdevicecooperate-getstate-f-sys.md) | 获取键鼠穿越开关的状态，使用Promise异步回调。 |
| [off_cooperation](arkts-input-inputdevicecooperate-offcooperation-f-sys.md#offcooperation) | 关闭监听键鼠穿越状态，使用callback异步回调。 |
| [on_cooperation](arkts-input-inputdevicecooperate-oncooperation-f-sys.md#oncooperation) | 注册监听键鼠穿越状态，使用callback异步回调。 |
| [start](arkts-input-inputdevicecooperate-start-f-sys.md) | 启动键鼠穿越，使用callback异步回调。 |
| [start](arkts-input-inputdevicecooperate-start-f-sys.md) | 启动键鼠穿越，使用Promise异步回调。 |
| [stop](arkts-input-inputdevicecooperate-stop-f-sys.md) | 停止键鼠穿越，使用callback异步回调。 |
| [stop](arkts-input-inputdevicecooperate-stop-f-sys.md) | 停止键鼠穿越，使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [EventMsg](arkts-input-inputdevicecooperate-eventmsg-e-sys.md) | 键鼠穿越事件。 |
<!--DelEnd-->

