# @ohos.multimodalInput.infraredEmitter(红外管理)

红外管理模块提供产生特定频率和大小的红外信号，以及查询设备支持的频率范围等功能。

**起始版本：** 12

<!--Device-unnamed-declare namespace infraredEmitter--><!--Device-unnamed-declare namespace infraredEmitter-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InfraredEmitter

## 导入模块

```TypeScript
import { infraredEmitter } from '@kit.InputKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getInfraredFrequencies](arkts-input-infraredemitter-getinfraredfrequencies-f.md#getinfraredfrequencies-1) | 查询设备支持的红外信号的频率范围。调用此接口前，需要先调用[hasIrEmitter](arkts-input-infraredemitter-hasiremitter-f.md)接口确认设备是否具备红外发射器。 |
| [hasIrEmitter](arkts-input-infraredemitter-hasiremitter-f.md#hasiremitter-1) | 查询设备是否配备红外发射器。使用Promise异步回调。 |
| [transmitInfrared](arkts-input-infraredemitter-transmitinfrared-f.md#transmitinfrared-1) | 产生特定频率和特定电平大小的红外信号。调用此接口前，需要先调用[hasIrEmitter](arkts-input-infraredemitter-hasiremitter-f.md)接口确认设备是否具备红外发射器。如果设备不具备红外发射器，调用本接口不生效。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [InfraredFrequency](arkts-input-infraredemitter-infraredfrequency-i.md) | 红外信号的频率范围。 |
