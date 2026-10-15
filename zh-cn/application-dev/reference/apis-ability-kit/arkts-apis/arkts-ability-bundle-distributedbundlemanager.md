# @ohos.bundle.distributedBundleManager(distributedBundleManager模块)

本模块提供分布式应用的管理能力。

**起始版本：** 9

<!--Device-unnamed-declare namespace distributedBundleManager--><!--Device-unnamed-declare namespace distributedBundleManager-End-->

**系统能力：** SystemCapability.BundleManager.DistributedBundleFramework

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { distributedBundleManager } from '@kit.AbilityKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getRemoteAbilityInfo](arkts-ability-distributedbundlemanager-getremoteabilityinfo-f-sys.md#getremoteabilityinfo1) | 获取由elementName指定的远程设备上的应用的AbilityInfo信息。使用callback异步回调。 |
| [getRemoteAbilityInfo](arkts-ability-distributedbundlemanager-getremoteabilityinfo-f-sys.md#getremoteabilityinfo2) | 获取由elementName指定的远程设备上的应用的AbilityInfo信息。使用Promise异步回调。 |
| [getRemoteAbilityInfo](arkts-ability-distributedbundlemanager-getremoteabilityinfo-f-sys.md#getremoteabilityinfo3) | 获取由elementNames指定的远程设备上的应用的AbilityInfo数组信息。使用callback异步回调。 |
| [getRemoteAbilityInfo](arkts-ability-distributedbundlemanager-getremoteabilityinfo-f-sys.md#getremoteabilityinfo4) | 获取由elementNames指定的远程设备上的应用的AbilityInfo数组信息。使用Promise异步回调。 |
| [getRemoteAbilityInfo](arkts-ability-distributedbundlemanager-getremoteabilityinfo-f-sys.md#getremoteabilityinfo5) | 获取由elementName和locale指定的远程设备上的应用的AbilityInfo信息。使用callback异步回调。 |
| [getRemoteAbilityInfo](arkts-ability-distributedbundlemanager-getremoteabilityinfo-f-sys.md#getremoteabilityinfo6) | 获取由elementName和locale指定的远程设备上的应用的AbilityInfo信息。使用Promise异步回调。 |
| [getRemoteAbilityInfo](arkts-ability-distributedbundlemanager-getremoteabilityinfo-f-sys.md#getremoteabilityinfo7) | 获取由elementNames和locale指定的远程设备上的应用的AbilityInfo数组信息。使用callback异步回调。 |
| [getRemoteAbilityInfo](arkts-ability-distributedbundlemanager-getremoteabilityinfo-f-sys.md#getremoteabilityinfo8) | 获取由elementNames和locale指定的远程设备上的应用的AbilityInfo数组信息。使用Promise异步回调。 |
| [getRemoteBundleVersionCode](arkts-ability-distributedbundlemanager-getremotebundleversioncode-f-sys.md#getremotebundleversioncode) | 获取指定远程设备上指定包名的应用版本号。使用Promise异步回调。 |
| [getRemoteMetadata](arkts-ability-distributedbundlemanager-getremotemetadata-f-sys.md#getremotemetadata) | 获取指定远程设备上指定包名的应用元数据信息。使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [RemoteAbilityInfo](arkts-ability-distributedbundlemanager-remoteabilityinfo-t-sys.md) | 包含远程的ability信息。 |
<!--DelEnd-->
