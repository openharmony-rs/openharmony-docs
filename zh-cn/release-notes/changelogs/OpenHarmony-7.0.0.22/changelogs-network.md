# 网络管理变更说明

## cl.network.1 getUidRxBytes、getUidTxBytes接口权限变更

**访问级别**

公共能力

**变更原因**

getUidRxBytes、getUidTxBytes接口需要添加权限管控。

**变更影响**

此变更涉及应用适配。

变更前：应用可通过本接口传入指定Uid查询其上下行流量数据。

变更后：若接口传入的Uid为自身应用Uid，则无需申请权限，接口行为与变更前一致；若接口传入的Uid非自身应用Uid时，需要申请ohos.permission.GET_NETWORK_STATS权限，其授权方式为system_grant，当前只允许MDM应用申请。


**起始 API Level**

API 10

**变更发生版本**

从OpenHarmony SDK 7.0.0.22开始。

**变更的接口/组件**

statistics.getUidRxBytes(uid: number, callback: AsyncCallback\<number\>): void
  
statistics.getUidRxBytes(uid: number): Promise\<number\>
  
statistics.getUidTxBytes(uid: number, callback: AsyncCallback\<number\>): void
  
statistics.getUidTxBytes(uid: number): Promise\<number\>

**适配指导**

1. 若应用仅使用上述接口查询自身流量，则无需适配；
2. 若非MDM应用使用上述接口查询其他应用流量，则需审视调用场景，若有影响需根据自身业务代码进行对应适配；
3. 若MDM应用使用上述接口查询其他应用流量，则需要申请ohos.permission.GET_NETWORK_STATS权限，接口其他行为与变更前一致。
