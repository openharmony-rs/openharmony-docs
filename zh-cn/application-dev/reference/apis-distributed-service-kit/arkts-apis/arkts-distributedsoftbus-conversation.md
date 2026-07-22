# @ohos.distributedSoftBus.conversation

分布式软总线conversation模块为应用提供跨设备交互能力，包括获取可信设备列表、发送和接收会话数据。通过本模块，应用可以获取同一账号下的可信设备，注册监听器以接收跨设备数据，并通过会话通道向指定设备发送数据。适用于需要跨设备协作和多设备数据传递的场景，可降低跨设备交互的开发复杂度。
> **说明：**  
>  
> 本模块接口为系统接口，仅可在Stage模型下使用。

**起始版本：** 26.1.0

<!--Device-unnamed-declare namespace conversation--><!--Device-unnamed-declare namespace conversation-End-->

**系统能力：** SystemCapability.Communication.SoftBus.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { conversation } from '@kit.DistributedServiceKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getTrustedDevices](arkts-distributedservice-conversation-gettrusteddevices-f-sys.md#gettrusteddevices) | 获取历史可信设备列表。典型使用场景包括：跨设备数据发送前查询可用目标设备。 |
| [postConversationData](arkts-distributedservice-conversation-postconversationdata-f-sys.md#postconversationdata) | 向目标设备发送会话数据。目标设备须为同一账号下的可信设备。以目标设备的networkId或UDID进行设备寻址，数据发送至目标设备上与指定Bundle名和Ability名匹配的已注册监听应用。典型使用场景包括：跨设备协同指令发送。 |
| [registerConversationListener](arkts-distributedservice-conversation-registerconversationlistener-f-sys.md#registerconversationlistener) | 注册会话监听，接收来自同一账号下可信设备的数据。当远端设备通过[postConversationData](arkts-distributedservice-conversation-postconversationdata-f-sys.md#postconversationdata)发送数据到达本地设备后，数据分发至与Bundle名和Ability名匹配的已注册回调函数。同一Bundle名和Ability名只能注册一个监听器，重复注册将覆盖之前已注册的监听器。  **配对调用**：需与注销监听器[unregisterConversationListener](arkts-distributedservice-conversation-unregisterconversationlistener-f-sys.md#unregisterconversationlistener)配对使用，不再需要接收消息时应调用注销监听器以释放资源，未注销会导致资源持续占用。 |
| [unregisterConversationListener](arkts-distributedservice-conversation-unregisterconversationlistener-f-sys.md#unregisterconversationlistener) | 注销指定Bundle名和Ability名的会话监听。需与注册监听器[registerConversationListener](arkts-distributedservice-conversation-registerconversationlistener-f-sys.md#registerconversationlistener)配对使用，用于注销已注册的会话监听器。在不再需要接收消息时应调用注销监听器以释放资源，未注销会导致资源持续占用。同一Bundle名和Ability名只能注册一个监听器，重复注册会覆盖之前的监听器，注销后将移除当前生效的监听器。调用此接口后，应用将不再接收对应Bundle名和Ability名的会话数据。如果之前未注册过指定Bundle名和Ability名的监听器，此接口同样返回成功。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DeviceNodeInfo](arkts-distributedservice-conversation-devicenodeinfo-i-sys.md) | 设备节点信息，包括networkId、设备名称、设备类型标识符、近场状态和UDID。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DataCallback](arkts-distributedservice-conversation-datacallback-t-sys.md) | 数据接收回调函数类型。 |
<!--DelEnd-->

