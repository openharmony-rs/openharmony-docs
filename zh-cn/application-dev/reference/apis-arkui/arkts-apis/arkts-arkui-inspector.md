# @ohos.arkui.inspector

提供注册组件布局和组件绘制送显完成回调通知的能力。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-declare namespace inspector--><!--Device-unnamed-declare namespace inspector-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getInspectorByKey](arkts-arkui-inspector-getinspectorbykey-f.md#getinspectorbykey) | 获取指定id组件的所有属性，不包括子组件信息。 此接口仅用于对应用的测试，使用时建议等应用启动且布局完成后再调用。由于耗时长，不建议测试之外的场景使用。 |
| [getInspectorTree](arkts-arkui-inspector-getinspectortree-f.md#getinspectortree) | 获取组件树及组件属性。 此接口仅用于对应用的测试。由于耗时长，不建议测试之外的场景使用。 |
| [sendEventByKey](arkts-arkui-inspector-sendeventbykey-f.md#sendeventbykey) | 给指定id的组件发送事件。 此接口仅用于对应用的测试。由于耗时长，不建议测试之外的场景使用。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ComponentObserver](arkts-arkui-inspector-componentobserver-i.md) | 组件布局和组件绘制送显完成回调的句柄，通过该句柄可调用以下方法。 |

