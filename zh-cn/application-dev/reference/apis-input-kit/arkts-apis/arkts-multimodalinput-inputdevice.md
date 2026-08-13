# @ohos.multimodalInput.inputDevice

本模块提供输入设备管理能力，包括监听输入设备的连接和断开状态，查询设备名称等输入设备信息。 > **说明：**

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace inputDevice--><!--Device-unnamed-declare namespace inputDevice-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getDevice](arkts-input-inputdevice-getdevice-f.md#getDevice) | 获取指定id的输入设备信息，使用callback异步回调。 |
| [getDevice](arkts-input-inputdevice-getdevice-f.md#getDevice) | 获取指定id的输入设备信息，使用Promise异步回调。 |
| [getDeviceIds](arkts-input-inputdevice-getdeviceids-f.md#getDeviceIds) | 获取所有输入设备的ID列表，使用callback异步回调。 |
| [getDeviceIds](arkts-input-inputdevice-getdeviceids-f.md#getDeviceIds) | 获取所有输入设备的ID列表，使用Promise异步回调。 |
| [getDeviceInfo](arkts-input-inputdevice-getdeviceinfo-f.md#getDeviceInfo) | 获取指定输入设备的信息，使用callback异步回调。 |
| [getDeviceInfo](arkts-input-inputdevice-getdeviceinfo-f.md#getDeviceInfo) | 获取指定id的输入设备信息，使用Promise异步回调。 |
| [getDeviceInfoSync](arkts-input-inputdevice-getdeviceinfosync-f.md#getDeviceInfoSync) | 获取指定输入设备的信息。 |
| [getDeviceList](arkts-input-inputdevice-getdevicelist-f.md#getDeviceList) | 获取所有输入设备的ID列表，使用callback异步回调。 |
| [getDeviceList](arkts-input-inputdevice-getdevicelist-f.md#getDeviceList) | 获取所有输入设备的ID列表，使用Promise异步回调。 |
| [getIntervalSinceLastInput](arkts-input-inputdevice-getintervalsincelastinput-f.md#getIntervalSinceLastInput) | 获取距离上次系统输入事件的时间间隔（包含设备休眠时间），使用Promise异步回调。 |
| [getKeyboardType](arkts-input-inputdevice-getkeyboardtype-f.md#getKeyboardType) | 获取输入设备的键盘类型，如全键盘、小键盘等。输入设备的键盘类型以接口返回结果为准。使用callback异步回调。 |
| [getKeyboardType](arkts-input-inputdevice-getkeyboardtype-f.md#getKeyboardType) | 获取输入设备的键盘类型，使用Promise异步回调。 |
| [getKeyboardTypeSync](arkts-input-inputdevice-getkeyboardtypesync-f.md#getKeyboardTypeSync) | 获取输入设备的键盘类型。 |
| [isFunctionKeyEnabled](arkts-input-inputdevice-isfunctionkeyenabled-f.md#isFunctionKeyEnabled) | 检查功能键（如：CapsLock键）是否使能。使用Promise异步回调。 |
| [offChange](arkts-input-inputdevice-offchange-f.md#offChange) | Stops listening for an input device event. |
| off_change | 取消监听输入设备的热插拔事件。在应用退出前调用，取消监听。使用callback异步回调。 |
| [onChange](arkts-input-inputdevice-onchange-f.md#onChange) | Starts listening for an input device event. |
| on_change | 注册监听输入设备的热插拔事件，使用时需连接鼠标、键盘、触摸屏等外部设备。使用callback异步回调。 |
| [setFunctionKeyEnabled](arkts-input-inputdevice-setfunctionkeyenabled-f.md#setFunctionKeyEnabled) | 设置功能键（如：CapsLock键）使能状态。使用Promise异步回调。 |
| [supportKeys](arkts-input-inputdevice-supportkeys-f.md#supportKeys) | 查询指定输入设备是否支持指定按键，使用callback异步回调。 |
| [supportKeys](arkts-input-inputdevice-supportkeys-f.md#supportKeys) | 查询指定输入设备是否支持指定按键，使用Promise异步回调。 |
| [supportKeysSync](arkts-input-inputdevice-supportkeyssync-f.md#supportKeysSync) | 查询指定id的输入设备对指定键值的支持情况。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getKeyboardRepeatDelay](arkts-input-inputdevice-getkeyboardrepeatdelay-f-sys.md#getKeyboardRepeatDelay) | 获取键盘按键的重复时延，使用callback异步回调。 |
| [getKeyboardRepeatDelay](arkts-input-inputdevice-getkeyboardrepeatdelay-f-sys.md#getKeyboardRepeatDelay（系统接口）) | 获取键盘按键的重复时延，使用Promise异步回调。 |
| [getKeyboardRepeatRate](arkts-input-inputdevice-getkeyboardrepeatrate-f-sys.md#getKeyboardRepeatRate) | 获取键盘按键的重复速率，使用callback异步回调。 |
| [getKeyboardRepeatRate](arkts-input-inputdevice-getkeyboardrepeatrate-f-sys.md#getKeyboardRepeatRate（系统接口）) | 获取键盘按键的重复速率，使用Promise异步回调。 |
| [setInputDeviceEnabled](arkts-input-inputdevice-setinputdeviceenabled-f-sys.md#setInputDeviceEnabled) | 设置输入设备的开关状态。以触摸屏为例：关闭时，点击触摸屏设备不响应；开启时，可正常操作触摸屏。使用Promise异步回调。 |
| [setKeyboardRepeatDelay](arkts-input-inputdevice-setkeyboardrepeatdelay-f-sys.md#setKeyboardRepeatDelay) | 设置键盘按键的重复时延，使用callback异步回调。 |
| [setKeyboardRepeatDelay](arkts-input-inputdevice-setkeyboardrepeatdelay-f-sys.md#setKeyboardRepeatDelay（系统接口）) | 设置键盘按键的重复时延，使用Promise异步回调。 |
| [setKeyboardRepeatRate](arkts-input-inputdevice-setkeyboardrepeatrate-f-sys.md#setKeyboardRepeatRate) | 设置键盘按键的重复速率，使用callback异步回调。 |
| [setKeyboardRepeatRate](arkts-input-inputdevice-setkeyboardrepeatrate-f-sys.md#setKeyboardRepeatRate（系统接口）) | 设置键盘按键的重复速率，使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AxisRange](arkts-input-inputdevice-axisrange-i.md) | 输入设备的轴信息。 |
| [DeviceListener](arkts-input-inputdevice-devicelistener-i.md) | 描述输入设备热插拔的信息。 |
| [InputDeviceData](arkts-input-inputdevice-inputdevicedata-i.md) | 描述输入设备的信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [FunctionKey](arkts-input-inputdevice-functionkey-e.md) | 功能键的类型。 |
| [KeyboardType](arkts-input-inputdevice-keyboardtype-e.md) | 键盘输入设备的类型。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [AxisType](arkts-input-inputdevice-axistype-t.md) | 输入设备的轴类型。 |
| [ChangedType](arkts-input-inputdevice-changedtype-t.md) | 监听设备热插拔事件类型。 |
| [SourceType](arkts-input-inputdevice-sourcetype-t.md) | 输入设备的输入能力。包括键盘、鼠标、触摸屏、轨迹球、触控板、操纵杆等。 |

