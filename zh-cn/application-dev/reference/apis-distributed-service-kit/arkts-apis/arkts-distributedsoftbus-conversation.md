# @ohos.distributedSoftBus.conversation(跨设备唤醒与消息传输)

/*
 Copyright (c) 2026 Huawei Device Co., Ltd.
 Licensed under the Apache License, Version 2.0 (the "License"),
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License at
 http://www.apache.org/licenses/LICENSE-2.0
 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS IS" BASIS,
 WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 See the License for the specific language governing permissions and
 limitations under the License.
 /


**起始版本：** 26.1.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.1.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace conversation--><!--Device-unnamed-declare namespace conversation-End-->

**系统能力：** SystemCapability.Communication.SoftBus.Core

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getTrustedDevices](arkts-distributedservice-conversation-gettrusteddevices-f-sys.md#getTrustedDevices) | 获取历史可信设备列表。典型使用场景包括：跨设备数据发送前查询可用目标设备。 |
| [postConversationData](arkts-distributedservice-conversation-postconversationdata-f-sys.md#postConversationData) | 向目标设备发送会话数据。目标设备须为同一账号下的可信设备。以目标设备的networkId或UDID进行设备寻址，数据发送至目标设备上 与指定Bundle名和Ability名匹配的已注册监听应用。典型使用场景包括：跨设备协同指令发送。 |
| [registerConversationListener](arkts-distributedservice-conversation-registerconversationlistener-f-sys.md#registerConversationListener) | 注册会话监听，接收来自同一账号下可信设备的数据。当远端设备通过 [postConversationData](arkts-distributedservice-conversation-postconversationdata-f-sys.md#postConversationData（系统接口）)发送数据到达本地设备后， 数据分发至与Bundle名和Ability名匹配的已注册回调函数。同一Bundle名和Ability名只能注册一个监听器，重复注册将覆盖 之前已注册的监听器。 **配对调用**：需与注销监听器[unregisterConversationListener](arkts-distributedservice-conversation-unregisterconversationlistener-f-sys.md#unregisterConversationListener（系统接口）)配对 使用，不再需要接收消息时应调用注销监听器以释放资源，未注销会导致资源持续占用。 |
| [unregisterConversationListener](arkts-distributedservice-conversation-unregisterconversationlistener-f-sys.md#unregisterConversationListener) | 注销指定Bundle名和Ability名的会话监听。需与注册监听器 [registerConversationListener](arkts-distributedservice-conversation-registerconversationlistener-f-sys.md#registerConversationListener（系统接口）)配对使用，用于注销已注册的会话监听器。 在不再需要接收消息时应调用注销监听器以释放资源，未注销会导致资源持续占用。同一Bundle名和Ability名只能注册一个监听器， 重复注册会覆盖之前的监听器，注销后将移除当前生效的监听器。调用此接口后，应用将不再接收对应Bundle名和Ability名的会话数据。 如果之前未注册过指定Bundle名和Ability名的监听器，此接口同样返回成功。 |
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

