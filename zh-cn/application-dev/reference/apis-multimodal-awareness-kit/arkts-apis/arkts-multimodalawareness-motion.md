# @ohos.multimodalAwareness.motion

**motion**模块提供用户动作感知能力，包括用户手势和动作。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace motion--><!--Device-unnamed-declare namespace motion-End-->

**系统能力：** SystemCapability.MultimodalAwareness.Motion

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getRecentOperatingHandStatus](arkts-multimodalawareness-motion-getrecentoperatinghandstatus-f.md#getRecentOperatingHandStatus) | 获取最新触控操作手状态。 |
| [offHoldingHandChanged](arkts-multimodalawareness-motion-offholdinghandchanged-f.md#offHoldingHandChanged) | 取消订阅握持手状态变化事件。 |
| [offOperatingHandChanged](arkts-multimodalawareness-motion-offoperatinghandchanged-f.md#offOperatingHandChanged) | 取消订阅触控操作手变化事件。 |
| off_holdingHandChanged | 取消订阅握持手状态变化感知事件。若未调用on()就调用off()，该方法会抛出异常。相关方法：on('holdingHandChanged')：订阅握持手状态变化感知事件。 |
| off_operatingHandChanged | 取消订阅触控操作手感知事件。若未调用on()就调用off()，该方法会抛出异常。相关方法：on('operatingHandChanged')：订阅触控操作手感知事件。 |
| [onHoldingHandChanged](arkts-multimodalawareness-motion-onholdinghandchanged-f.md#onHoldingHandChanged) | 订阅握持手状态变化事件。 |
| [onOperatingHandChanged](arkts-multimodalawareness-motion-onoperatinghandchanged-f.md#onOperatingHandChanged) | 订阅触控操作手变化事件。 |
| on_holdingHandChanged | 订阅握持手状态变化感知事件。调用on()订阅事件后，建议在使用完毕后调用off()取消订阅以释放资源，避免多余的性能功耗开销。相关方法：off('holdingHandChanged')：取消订阅握持手状态变化感知事件。 |
| on_operatingHandChanged | 订阅触控操作手感知事件。调用on()订阅事件后，建议在使用完毕后调用off()取消订阅以释放资源，避免多余的性能功耗开销。相关方法：off('operatingHandChanged')：取消订阅触控操作手感知事件。 如果设备不支持此功能，将返回801错误码。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [offHoverHandChange](arkts-multimodalawareness-motion-offhoverhandchange-f-sys.md#offHoverHandChange) | 取消订阅悬停手势事件。 |
| [offPickupChange](arkts-multimodalawareness-motion-offpickupchange-f-sys.md#offPickupChange) | 取消订阅拾起传感器事件。 |
| [offRotateChange](arkts-multimodalawareness-motion-offrotatechange-f-sys.md#offRotateChange) | 取消订阅旋转传感器事件。 |
| [offSmartRotateChange](arkts-multimodalawareness-motion-offsmartrotatechange-f-sys.md#offSmartRotateChange) | 取消订阅智能旋转传感器事件。 |
| [onHoverHandChange](arkts-multimodalawareness-motion-onhoverhandchange-f-sys.md#onHoverHandChange) | 订阅悬停手势事件，并立即开始5秒检测。 |
| [onHoverHandChange](arkts-multimodalawareness-motion-onhoverhandchange-f-sys.md#onHoverHandChange（系统接口）) | 订阅悬停手势事件，并立即开始检测。 |
| [onPickupChange](arkts-multimodalawareness-motion-onpickupchange-f-sys.md#onPickupChange) | 订阅拾起传感器事件。 |
| [onRotateChange](arkts-multimodalawareness-motion-onrotatechange-f-sys.md#onRotateChange) | 订阅旋转传感器事件。 |
| [onSmartRotateChange](arkts-multimodalawareness-motion-onsmartrotatechange-f-sys.md#onSmartRotateChange) | 订阅智能旋转传感器事件。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [HoverHandDetectionArea](arkts-multimodalawareness-motion-hoverhanddetectionarea-i-sys.md) | 悬停手势检测区域的基础数据结构。 |
| [SmartRotateEvent](arkts-multimodalawareness-motion-smartrotateevent-i-sys.md) | 智能旋转传感器事件的基础数据结构。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [HoldingHandStatus](arkts-multimodalawareness-motion-holdinghandstatus-e.md) | 握持手状态信息，表示握持手状态变化感知事件的结果。订阅握持手状态变化感知事件后，返回当前握持手状态信息。 |
| [OperatingHandStatus](arkts-multimodalawareness-motion-operatinghandstatus-e.md) | 触控操作手状态信息。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [HoverHandAction](arkts-multimodalawareness-motion-hoverhandaction-e-sys.md) | 悬停手势动作枚举。 |
| [LogicalOrientation](arkts-multimodalawareness-motion-logicalorientation-e-sys.md) | 智能算法计算得到的逻辑方向枚举。 |
| [PhysicalOrientation](arkts-multimodalawareness-motion-physicalorientation-e-sys.md) | 传感器检测到的物理方向枚举。 |
| [PickupEvent](arkts-multimodalawareness-motion-pickupevent-e-sys.md) | 拾起事件枚举。 |
| [RotateEvent](arkts-multimodalawareness-motion-rotateevent-e-sys.md) | 旋转事件枚举。 |
<!--DelEnd-->

