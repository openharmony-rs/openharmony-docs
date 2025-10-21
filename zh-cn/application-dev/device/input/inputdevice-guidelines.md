# 输入设备开发指导

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

## 场景介绍

输入设备管理提供设备热插拔监听、查询指定设备的键盘类型等能力。使用场景例如：当用户需要输入文本时，输入法会根据当前是否插入了物理键盘来决定是否弹出虚拟键盘，开发者可以通过监听设备热插拔判断是否有物理键盘插入。

## 导入模块

```js
import { inputDevice } from '@kit.InputKit';
```

## 接口说明

输入设备管理常用接口如下表所示，接口详细介绍请参考[ohos.multimodalInput.inputDevice文档](../../reference/apis-input-kit/js-apis-inputdevice.md)。

| 接口名称  | 描述 |
| ----------- | ------------------------------------------------------------ | 
| getDeviceList(): Promise\<Array\<number>> | 获取输入设备列表。 |
| getKeyboardType(deviceId: number): Promise\<KeyboardType> | 获取输入设备的键盘类型。 |
| on(type: "change", listener: Callback\<DeviceListener>): void | 监听输入设备的热插拔事件。 |
| off(type: "change", listener?: Callback\<DeviceListener>): void | 取消监听输入设备的热插拔事件。 |

## 虚拟键盘弹出检测

当用户需要输入文本时，输入法会根据当前是否插入了物理键盘来决定是否弹出虚拟键盘，开发者可以通过监听设备热插拔，判断是否有物理键盘插入。

### 开发步骤

1. 调用[getDeviceList](../../reference/apis-input-kit/js-apis-inputdevice.md#inputdevicegetdevicelist9)方法查询所有连接的输入设备，调用[getKeyboardType](../../reference/apis-input-kit/js-apis-inputdevice.md#inputdevicegetkeyboardtype9)方法遍历所有连接的设备，判断是否有物理键盘，若有则标记已有物理键盘连接，该步骤确保监听设备热插拔之前，检测所有插入的输入设备。
2. 调用[on](../../reference/apis-input-kit/js-apis-inputdevice.md#inputdeviceon9)接口监听输入设备热插拔事件，若监听到有物理键盘插入，则标记已有物理键盘连接；若监听到有物理键盘拔掉，则标记没有物理键盘连接。

<!-- @[input_device](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/input/ArkTSInputDevice/entry/src/main/ets/pages/Index.ets) -->
