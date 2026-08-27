# @ohos.multimodalInput.infraredEmitter(红外管理)

红外管理模块提供产生特定频率和大小的红外信号，以及查询设备支持的频率范围等功能。

**起始版本：** 12

**系统能力：** SystemCapability.MultimodalInput.Input.InfraredEmitter

## 导入模块

```TypeScript
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getInfraredFrequencies(红外管理)](arkts-input-infraredemitter-getinfraredfrequencies-f.md) | 查询设备支持的红外信号的频率范围。建议先使用[hasIrEmitter]接口查询设备是否支持红外发射器。 |
| [hasIrEmitter(红外管理)](arkts-input-infraredemitter-hasiremitter-f.md) | 查询设备是否配备红外发射器。使用Promise异步回调。 |
| [transmitInfrared(红外管理)](arkts-input-infraredemitter-transmitinfrared-f.md) | 产生特定频率和特定电平大小的红外信号。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [InfraredFrequency(红外管理)](arkts-input-infraredemitter-infraredfrequency-i.md) | 红外信号的频率范围。 |
