# @ohos.distributedHardware.hardwareManager

分布式硬件管理模块提供控制分布式硬件的能力，包括暂停、恢复和停止被控端分布式硬件业务。

**起始版本：** 11

<!--Device-unnamed-declare namespace hardwareManager--><!--Device-unnamed-declare namespace hardwareManager-End-->

**系统能力：** SystemCapability.DistributedHardware.DistributedHardwareFWK

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { hardwareManager } from '@kit.DistributedServiceKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [pauseDistributedHardware](arkts-distributedservice-hardwaremanager-pausedistributedhardware-f-sys.md#pausedistributedhardware) | 暂停被控端分布式硬件业务。使用promise异步回调。 |
| [resumeDistributedHardware](arkts-distributedservice-hardwaremanager-resumedistributedhardware-f-sys.md#resumedistributedhardware) | 恢复被控端分布式硬件业务。使用promise异步回调。 |
| [stopDistributedHardware](arkts-distributedservice-hardwaremanager-stopdistributedhardware-f-sys.md#stopdistributedhardware) | 停止被控端分布式硬件业务。使用promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [HardwareDescriptor](arkts-distributedservice-hardwaremanager-hardwaredescriptor-i-sys.md) | 表示分布式硬件的描述信息。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DistributedHardwareErrorCode](arkts-distributedservice-hardwaremanager-distributedhardwareerrorcode-e-sys.md) | 分布式硬件错误码的枚举。 |
| [DistributedHardwareType](arkts-distributedservice-hardwaremanager-distributedhardwaretype-e-sys.md) | 表示分布式硬件类型。 |
<!--DelEnd-->

