# @ohos.distributedHardware.hardwareManager(分布式硬件管理)

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
| [pauseDistributedHardware](arkts-distributedservice-hardwaremanager-pausedistributedhardware-f-sys.md#pausedistributedhardware-1) | 暂停被控端分布式硬件业务。被控端指通过分布式能力连接的远端设备，分布式硬件业务指通过分布式能力调用的相机、麦克风等硬件功能。使用promise异步回调，暂停后可以调用resumeDistributedHardware恢复业务或stopDistributedHardware停止业务。调用此方法前需确保分布式硬件已启动。使用场景：在多设备协同场景下临时暂停某些设备的硬件功能（如暂停远端相机以节省带宽）；当系统资源紧张时暂停非关键的分布式硬件以释放资源；切换设备配置时暂时停止当前硬件同步。 |
| [resumeDistributedHardware](arkts-distributedservice-hardwaremanager-resumedistributedhardware-f-sys.md#resumedistributedhardware-1) | 恢复被控端分布式硬件业务。被控端对应的分布式硬件业务恢复正常运行。使用promise异步回调，必须在pauseDistributedHardware暂停后调用，用于恢复已暂停的业务。调用此方法前需确保分布式硬件已启动。使用场景：当多设备协同场景下需要重新启用已暂停的硬件功能时；当系统资源恢复后重新激活非关键分布式硬件时；切换设备配置完成时恢复硬件同步功能。 |
| [stopDistributedHardware](arkts-distributedservice-hardwaremanager-stopdistributedhardware-f-sys.md#stopdistributedhardware-1) | 停止被控端分布式硬件业务。被控端对应的分布式硬件业务停止。使用promise异步回调。停止后无法通过resumeDistributedHardware恢复业务，需要重新启动分布式硬件服务，不能再调用pauseDistributedHardware或resumeDistributedHardware。调用此方法前需确保分布式硬件已启动。使用场景：当应用退出或不再需要分布式硬件功能时；当用户主动关闭分布式硬件服务时；当设备断开连接需要释放分布式硬件资源时。 |
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
| [DistributedHardwareType](arkts-distributedservice-hardwaremanager-distributedhardwaretype-e-sys.md) | 指定要操作的分布式硬件类型，决定暂停、恢复或停止操作的硬件范围。例如，设置为CAMERA时仅操作分布式相机，设置为ALL时操作所有分布式硬件。使用该参数前需确保对应的分布式硬件服务已启动。 |
<!--DelEnd-->
