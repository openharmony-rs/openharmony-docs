# @ohos.multimodalInput.inputDevice(输入设备)

本模块提供输入设备管理能力，包括监听输入设备的连接和断开状态，查询设备名称等输入设备信息。

**起始版本：** 8

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

## 导入模块

```TypeScript
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getDevice(输入设备)](arkts-input-inputdevice-getdevice-f.md) | 获取指定id的输入设备信息，使用callback异步回调。 |
| [getDevice(输入设备)](arkts-input-inputdevice-getdevice-f.md) | 获取指定id的输入设备信息，使用Promise异步回调。 |
| [getDeviceIds(输入设备)](arkts-input-inputdevice-getdeviceids-f.md) | 获取所有输入设备的ID列表，使用callback异步回调。 |
| [getDeviceIds(输入设备)](arkts-input-inputdevice-getdeviceids-f.md) | 获取所有输入设备的ID列表，使用Promise异步回调。 |
| [getDeviceInfo(输入设备)](arkts-input-inputdevice-getdeviceinfo-f.md) | 获取指定输入设备的信息，使用callback异步回调。 |
| [getDeviceInfo(输入设备)](arkts-input-inputdevice-getdeviceinfo-f.md) | 获取指定id的输入设备信息，使用Promise异步回调。 |
| [getDeviceInfoSync(输入设备)](arkts-input-inputdevice-getdeviceinfosync-f.md) | 获取指定输入设备的信息。 |
| [getDeviceList(输入设备)](arkts-input-inputdevice-getdevicelist-f.md) | 获取所有输入设备的ID列表，使用callback异步回调。 |
| [getDeviceList(输入设备)](arkts-input-inputdevice-getdevicelist-f.md) | 获取所有输入设备的ID列表，使用Promise异步回调。 |
| [getIntervalSinceLastInput(输入设备)](arkts-input-inputdevice-getintervalsincelastinput-f.md) | 获取距离上次系统输入事件的时间间隔（包含设备休眠时间），使用Promise异步回调。 |
| [getKeyboardType(输入设备)](arkts-input-inputdevice-getkeyboardtype-f.md) | 获取输入设备的键盘类型，如全键盘、小键盘等。输入设备的键盘类型以接口返回结果为准。使用callback异步回调。 |
| [getKeyboardType(输入设备)](arkts-input-inputdevice-getkeyboardtype-f.md) | 获取输入设备的键盘类型，使用Promise异步回调。 |
| [getKeyboardTypeSync(输入设备)](arkts-input-inputdevice-getkeyboardtypesync-f.md) | 获取输入设备的键盘类型。 |
| [isFunctionKeyEnabled(输入设备)](arkts-input-inputdevice-isfunctionkeyenabled-f.md) | 检查功能键（如：CapsLock键）是否使能。使用Promise异步回调。 |
| [off(输入设备)](arkts-input-inputdevice-off-f.md#offchange) | 取消监听输入设备的热插拔事件。在应用退出前调用，取消监听。使用callback异步回调。 |
| [on(输入设备)](arkts-input-inputdevice-on-f.md#onchange) | 注册监听输入设备的热插拔事件，使用时需连接鼠标、键盘、触摸屏等外部设备。使用callback异步回调。 |
| [setFunctionKeyEnabled(输入设备)](arkts-input-inputdevice-setfunctionkeyenabled-f.md) | 设置功能键（如：CapsLock键）使能状态。使用Promise异步回调。 |
| [supportKeys(输入设备)](arkts-input-inputdevice-supportkeys-f.md) | 查询指定输入设备是否支持指定按键，使用callback异步回调。 |
| [supportKeys(输入设备)](arkts-input-inputdevice-supportkeys-f.md) | 查询指定输入设备是否支持指定按键，使用Promise异步回调。 |
| [supportKeysSync(输入设备)](arkts-input-inputdevice-supportkeyssync-f.md) | 查询指定id的输入设备对指定键值的支持情况。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [bindToDisplay(输入设备)](arkts-input-inputdevice-bindtodisplay-f-sys.md) | 将输入设备绑定到显示器。仅支持外接USB和蓝牙的鼠标、触摸板、键盘和游戏手柄。绑定后，输入设备将固定在指定显示器所在的显示器组上操作。使用Promise异步回调。 |
| [getKeyboardRepeatDelay(输入设备)](arkts-input-inputdevice-getkeyboardrepeatdelay-f-sys.md) | 获取键盘按键的重复时延，使用callback异步回调。 |
| [getKeyboardRepeatDelay(输入设备)](arkts-input-inputdevice-getkeyboardrepeatdelay-f-sys.md) | 获取键盘按键的重复时延，使用Promise异步回调。 |
| [getKeyboardRepeatRate(输入设备)](arkts-input-inputdevice-getkeyboardrepeatrate-f-sys.md) | 获取键盘按键的重复速率，使用callback异步回调。 |
| [getKeyboardRepeatRate(输入设备)](arkts-input-inputdevice-getkeyboardrepeatrate-f-sys.md) | 获取键盘按键的重复速率，使用Promise异步回调。 |
| [setInputDeviceEnabled(输入设备)](arkts-input-inputdevice-setinputdeviceenabled-f-sys.md) | 设置输入设备的开关状态。以触摸屏为例：关闭时，点击触摸屏设备不响应；开启时，可正常操作触摸屏。使用Promise异步回调。 |
| [setKeyboardRepeatDelay(输入设备)](arkts-input-inputdevice-setkeyboardrepeatdelay-f-sys.md) | 设置键盘按键的重复时延，使用callback异步回调。 |
| [setKeyboardRepeatDelay(输入设备)](arkts-input-inputdevice-setkeyboardrepeatdelay-f-sys.md) | 设置键盘按键的重复时延，使用Promise异步回调。 |
| [setKeyboardRepeatRate(输入设备)](arkts-input-inputdevice-setkeyboardrepeatrate-f-sys.md) | 设置键盘按键的重复速率，使用callback异步回调。 |
| [setKeyboardRepeatRate(输入设备)](arkts-input-inputdevice-setkeyboardrepeatrate-f-sys.md) | 设置键盘按键的重复速率，使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AxisRange(输入设备)](arkts-input-inputdevice-axisrange-i.md) | 输入设备的轴信息。 |
| [DeviceListener(输入设备)](arkts-input-inputdevice-devicelistener-i.md) | 描述输入设备热插拔的信息。 |
| [InputDeviceData(输入设备)](arkts-input-inputdevice-inputdevicedata-i.md) | 描述输入设备的信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [FunctionKey(输入设备)](arkts-input-inputdevice-functionkey-e.md) | 功能键的类型。 |
| [KeyboardType(输入设备)](arkts-input-inputdevice-keyboardtype-e.md) | 键盘输入设备的类型。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [AxisType(输入设备)](arkts-input-inputdevice-axistype-t.md) | 输入设备的轴类型。 |
| [ChangedType(输入设备)](arkts-input-inputdevice-changedtype-t.md) | 监听设备热插拔事件类型。 |
| [SourceType(输入设备)](arkts-input-inputdevice-sourcetype-t.md) | 输入设备的输入能力。包括键盘、鼠标、触摸屏、轨迹球、触控板、操纵杆等。 |
