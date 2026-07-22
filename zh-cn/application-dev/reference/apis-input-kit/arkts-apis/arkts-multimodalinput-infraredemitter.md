# @ohos.multimodalInput.infraredEmitter

红外管理模块提供产生特定频率和大小的红外信号，以及查询设备支持的频率范围等功能。
> **说明**：

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
| [hasIrEmitter](arkts-input-infraredemitter-hasiremitter-f.md#hasiremitter) | 查询设备是否配备红外发射器。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getInfraredFrequencies](arkts-input-infraredemitter-getinfraredfrequencies-f-sys.md#getinfraredfrequencies) | 查询设备支持的红外信号的频率范围。 |
| [transmitInfrared](arkts-input-infraredemitter-transmitinfrared-f-sys.md#transmitinfrared) | 产生特定频率和特定电平大小的红外信号。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [InfraredFrequency](arkts-input-infraredemitter-infraredfrequency-i-sys.md) | 红外信号的频率范围。 |
<!--DelEnd-->

