# @ohos.multimodalAwareness.motion

**motion**本模块提供对用户手势识别、设备姿态监听等感知能力，适用于需要根据用户手势或动作进行响应的交互场景，如握持手、设备拾起等，帮助应用提供更自然的交互体验和精准的场景感知。

**起始版本：** 23

<!--Device-unnamed-declare namespace motion--><!--Device-unnamed-declare namespace motion-End-->

**系统能力：** SystemCapability.MultimodalAwareness.Motion

## 导入模块

```TypeScript
import { motion } from '@kit.MultimodalAwarenessKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getRecentOperatingHandStatus](arkts-multimodalawareness-motion-getrecentoperatinghandstatus-f.md) | 获取最新触控操作手状态。该方法直接返回最新的操作手状态，无需订阅事件即可调用。 |
| [offHoldingHandChanged](arkts-multimodalawareness-motion-offholdinghandchanged-f.md) | 取消订阅握持手状态变化事件。 |
| [offOperatingHandChanged](arkts-multimodalawareness-motion-offoperatinghandchanged-f.md) | 取消订阅触控操作手变化事件。 |
| [off_holdingHandChanged](arkts-multimodalawareness-motion-offholdinghandchanged-f.md) | 取消订阅握持手状态变化感知事件。若未调用on()就调用off()，该方法会抛出异常。相关方法：on('holdingHandChanged')：订阅握持手状态变化感知事件。 |
| [off_operatingHandChanged](arkts-multimodalawareness-motion-offoperatinghandchanged-f.md) | 取消订阅触控操作手感知事件。若未调用on()就调用off()，该方法会抛出异常。相关方法：on('operatingHandChanged')：订阅触控操作手感知事件。 |
| [onHoldingHandChanged](arkts-multimodalawareness-motion-onholdinghandchanged-f.md) | 订阅握持手状态变化事件。 |
| [onOperatingHandChanged](arkts-multimodalawareness-motion-onoperatinghandchanged-f.md) | 订阅触控操作手变化事件。 |
| [on_holdingHandChanged](arkts-multimodalawareness-motion-onholdinghandchanged-f.md) | 订阅握持手状态变化感知事件。系统通过传感器数据，结合识别算法判断当前握持手是左手还是右手。适用于阅读应用、视频播放等需要根据用户握持手状态调整界面布局或功能的场景。 <br>建议在使用完毕后调用off()取消订阅以释放资源，避免多余的性能功耗开销。相关方法：off('holdingHandChanged')：取消订阅握持手状态变化感知事件。 |
| [on_operatingHandChanged](arkts-multimodalawareness-motion-onoperatinghandchanged-f.md) | 订阅触控操作手感知事件。系统通过触控屏传感器采集用户触控数据，结合手势识别算法判断当前操作手是左手还是右手。适用于手势交付、单双手操作适配等场景， <br>通过识别用户的触控操作手状态优化界面布局和交互方式。建议在使用完毕后调用off()取消订阅以释放资源，避免多余的性能功耗开销。 <br>相关方法：off('operatingHandChanged')：取消订阅触控操作手感知事件。 如果设备不支持此功能，将返回801错误码。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [offHoverHandChange](arkts-multimodalawareness-motion-offhoverhandchange-f-sys.md) | 取消订阅悬停手势事件。 |
| [offPickupChange](arkts-multimodalawareness-motion-offpickupchange-f-sys.md) | 取消订阅拾起传感器事件。 |
| [offRotateChange](arkts-multimodalawareness-motion-offrotatechange-f-sys.md) | 取消订阅旋转传感器事件。 |
| [offSmartRotateChange](arkts-multimodalawareness-motion-offsmartrotatechange-f-sys.md) | 取消订阅智能旋转传感器事件。 |
| [onHoverHandChange](arkts-multimodalawareness-motion-onhoverhandchange-f-sys.md) | 订阅悬停手势事件，并立即开始5秒检测。 |
| [onHoverHandChange](arkts-multimodalawareness-motion-onhoverhandchange-f-sys.md) | 订阅悬停手势事件，并立即开始检测。 |
| [onPickupChange](arkts-multimodalawareness-motion-onpickupchange-f-sys.md) | 订阅拾起传感器事件。 |
| [onRotateChange](arkts-multimodalawareness-motion-onrotatechange-f-sys.md) | 订阅旋转传感器事件。 |
| [onSmartRotateChange](arkts-multimodalawareness-motion-onsmartrotatechange-f-sys.md) | 订阅智能旋转传感器事件。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [HoverHandDetectionArea](arkts-multimodalawareness-motion-hoverhanddetectionarea-i-sys.md) | 悬浮手矩形检测区域的基本数据结构。 |
| [SmartRotateEvent](arkts-multimodalawareness-motion-smartrotateevent-i-sys.md) | 智能旋转传感器事件的基本数据结构。该事件包含传感器检测到的物理方向和由智能算法计算得出的逻辑方向。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [HoldingHandStatus](arkts-multimodalawareness-motion-holdinghandstatus-e.md) | 握持手状态信息，表示握持手状态变化感知事件的结果。订阅事件后，返回当前握持手状态信息。 |
| [OperatingHandStatus](arkts-multimodalawareness-motion-operatinghandstatus-e.md) | 触控操作手状态信息。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [HoverHandAction](arkts-multimodalawareness-motion-hoverhandaction-e-sys.md) | 悬浮手动作枚举。 |
| [LogicalOrientation](arkts-multimodalawareness-motion-logicalorientation-e-sys.md) | 由智能算法计算出的逻辑方向枚举。 |
| [PhysicalOrientation](arkts-multimodalawareness-motion-physicalorientation-e-sys.md) | 传感器检测到的物理方向枚举。 |
| [PickupEvent](arkts-multimodalawareness-motion-pickupevent-e-sys.md) | 拾取事件枚举。 |
| [RotateEvent](arkts-multimodalawareness-motion-rotateevent-e-sys.md) | 旋转事件枚举。 |
<!--DelEnd-->

