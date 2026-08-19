# @ohos.multimodalInput.infraredEmitter(红外管理)

红外管理模块提供产生特定频率和大小的红外信号，以及查询设备支持的频率范围等功能。

**起始版本：** 23

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
| [hasIrEmitter(红外管理)](arkts-input-infraredemitter-hasiremitter-f.md) | 查询设备是否配备红外发射器。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getInfraredFrequencies(红外管理)](arkts-input-infraredemitter-getinfraredfrequencies-f-sys.md) | 查询设备支持的红外信号的频率范围。建议先使用[hasIrEmitter]接口查询设备是否支持红外发射器。 |
| [transmitInfrared(红外管理)](arkts-input-infraredemitter-transmitinfrared-f-sys.md) | 产生特定频率和特定电平大小的红外信号。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [InfraredFrequency(红外管理)](arkts-input-infraredemitter-infraredfrequency-i-sys.md) | 红外信号的频率范围。 |
<!--DelEnd-->

