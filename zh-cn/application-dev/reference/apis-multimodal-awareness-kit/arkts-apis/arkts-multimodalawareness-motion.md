# @ohos.multimodalAwareness.motion(动作感知能力)

**motion**本模块提供对用户手势识别、设备姿态监听等感知能力，适用于需要根据用户手势或动作进行响应的交互场景，如握持手、设备拾起等，帮助应用提供更自然的交互体验和精准的场景感知。

**起始版本：** 15

**系统能力：** SystemCapability.MultimodalAwareness.Motion

## 导入模块

```TypeScript
import { motion } from '@kit.MultimodalAwarenessKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getRecentOperatingHandStatus(动作感知能力)](arkts-multimodalawareness-motion-getrecentoperatinghandstatus-f.md) | 获取最新触控操作手状态。该方法直接返回最新的操作手状态，无需订阅事件即可调用。 |
| [off(动作感知能力)](arkts-multimodalawareness-motion-off-f.md#offoperatinghandchanged) | 取消订阅触控操作手感知事件。若未调用on()就调用off()，该方法会抛出异常。相关方法：on('operatingHandChanged')：订阅触控操作手感知事件。 |
| [off(动作感知能力)](arkts-multimodalawareness-motion-off-f.md#offholdinghandchanged) | 取消订阅握持手状态变化感知事件。若未调用on()就调用off()，该方法会抛出异常。相关方法：on('holdingHandChanged')：订阅握持手状态变化感知事件。 |
| [on(动作感知能力)](arkts-multimodalawareness-motion-on-f.md#onoperatinghandchanged) | 订阅触控操作手感知事件。系统通过触控屏传感器采集用户触控数据，结合手势识别算法判断当前操作手是左手还是右手。适用于手势交付、单双手操作适配等场景， 通过识别用户的触控操作手状态优化界面布局和交互方式。建议在使用完毕后调用off()取消订阅以释放资源，避免多余的性能功耗开销。 相关方法：off('operatingHandChanged')：取消订阅触控操作手感知事件。如果设备不支持此功能，将返回801错误码。 |
| [on(动作感知能力)](arkts-multimodalawareness-motion-on-f.md#onholdinghandchanged) | 订阅握持手状态变化感知事件。系统通过传感器数据，结合识别算法判断当前握持手是左手还是右手。适用于阅读应用、视频播放等需要根据用户握持手状态调整界面布局或功能的场景。 建议在使用完毕后调用off()取消订阅以释放资源，避免多余的性能功耗开销。相关方法：off('holdingHandChanged')：取消订阅握持手状态变化感知事件。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [offHoverHandChange(动作感知能力)](arkts-multimodalawareness-motion-offhoverhandchange-f-sys.md) | 取消订阅悬停手势事件。 |
| [offPickupChange(动作感知能力)](arkts-multimodalawareness-motion-offpickupchange-f-sys.md) | 取消订阅拾起传感器事件。 |
| [offRotateChange(动作感知能力)](arkts-multimodalawareness-motion-offrotatechange-f-sys.md) | 取消订阅旋转传感器事件。 |
| [offSmartRotateChange(动作感知能力)](arkts-multimodalawareness-motion-offsmartrotatechange-f-sys.md) | 取消订阅智能旋转传感器事件。 |
| [onHoverHandChange(动作感知能力)](arkts-multimodalawareness-motion-onhoverhandchange-f-sys.md) | 订阅悬停手势事件，并立即开始5秒检测。 |
| [onHoverHandChange(动作感知能力)](arkts-multimodalawareness-motion-onhoverhandchange-f-sys.md) | 订阅悬停手势事件，并立即开始检测。 |
| [onPickupChange(动作感知能力)](arkts-multimodalawareness-motion-onpickupchange-f-sys.md) | 订阅拾起传感器事件。 |
| [onRotateChange(动作感知能力)](arkts-multimodalawareness-motion-onrotatechange-f-sys.md) | 订阅旋转传感器事件。 |
| [onSmartRotateChange(动作感知能力)](arkts-multimodalawareness-motion-onsmartrotatechange-f-sys.md) | 订阅智能旋转传感器事件。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [HoverHandDetectionArea(动作感知能力)](arkts-multimodalawareness-motion-hoverhanddetectionarea-i-sys.md) | 悬浮手矩形检测区域的基本数据结构。 |
| [SmartRotateEvent(动作感知能力)](arkts-multimodalawareness-motion-smartrotateevent-i-sys.md) | 智能旋转传感器事件的基本数据结构。该事件包含传感器检测到的物理方向和由智能算法计算得出的逻辑方向。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [HoldingHandStatus(动作感知能力)](arkts-multimodalawareness-motion-holdinghandstatus-e.md) | 握持手状态信息，表示握持手状态变化感知事件的结果。订阅事件后，返回当前握持手状态信息。 |
| [OperatingHandStatus(动作感知能力)](arkts-multimodalawareness-motion-operatinghandstatus-e.md) | 触控操作手状态信息。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [HoverHandAction(动作感知能力)](arkts-multimodalawareness-motion-hoverhandaction-e-sys.md) | 悬浮手动作枚举。 |
| [LogicalOrientation(动作感知能力)](arkts-multimodalawareness-motion-logicalorientation-e-sys.md) | 由智能算法计算出的逻辑方向枚举。 |
| [PhysicalOrientation(动作感知能力)](arkts-multimodalawareness-motion-physicalorientation-e-sys.md) | 传感器检测到的物理方向枚举。 |
| [PickupEvent(动作感知能力)](arkts-multimodalawareness-motion-pickupevent-e-sys.md) | 拾取事件枚举。 |
| [RotateEvent(动作感知能力)](arkts-multimodalawareness-motion-rotateevent-e-sys.md) | 旋转事件枚举。 |
<!--DelEnd-->
