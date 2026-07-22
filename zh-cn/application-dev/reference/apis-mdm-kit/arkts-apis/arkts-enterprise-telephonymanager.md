# @ohos.enterprise.telephonyManager

本模块提供通话管理能力。
> **说明**：  
>  
> 本模块接口仅适用于Stage模型。  
>  
> 本模块接口仅对设备管理应用开放，调用接口前需激活该应用，详情请参考[MDM Kit开发指南](../../../mdm/mdm-kit-guide.md)。  
>  
> 全局通用限制类策略由restrictions提供，若要全局禁用通话，请参考  
> [@ohos.enterprise.restrictions （限制类策略）](arkts-enterprise-restrictions.md)。

**起始版本：** 20

<!--Device-unnamed-declare namespace telephonyManager--><!--Device-unnamed-declare namespace telephonyManager-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { telephonyManager } from '@kit.MDMKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [activeSim](arkts-mdm-telephonymanager-activesim-f.md#activesim) | 启用指定卡槽的SIM卡。设备已经插入SIM卡但是并未启用的场景，可以通过该接口启用SIM卡，无需用户手动启用。SIM卡启用后可以使用该SIM卡进行通信。该接口需要插入SIM卡并关闭飞行模式才能成功调用。 |
| [addIncomingCallPolicyNumbers](arkts-mdm-telephonymanager-addincomingcallpolicynumbers-f.md#addincomingcallpolicynumbers) | 添加通话呼入的允许或禁用名单，如果不添加名单，则任意号码都可以呼入，添加后仅名单内的号码允许或禁止呼入。  以下情况下，通过本接口添加通话呼入的允许或禁用名单，会报策略冲突：  1. 已经通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy)接口禁用了设备通话能力，再通过本接口添加通话呼入的禁用或允许名单，返回203错误码。通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy)接口解除禁用设备通话能力后，可解除冲突。2. 已经通过本接口设置了通话呼入的禁用名单，再通过本接口添加通话呼入允许名单，返回9200010错误码。通过[removeIncomingCallPolicyNumbers](arkts-mdm-telephonymanager-removeincomingcallpolicynumbers-f.md#removeincomingcallpolicynumbers)接口将之前设置的通话呼入禁用名单移除后，可解除冲突。3. 已经通过本接口设置了通话呼入的允许名单，再通过本接口添加通话呼入禁用名单，返回9200010错误码。通过[removeIncomingCallPolicyNumbers](arkts-mdm-telephonymanager-removeincomingcallpolicynumbers-f.md#removeincomingcallpolicynumbers)接口将之前设置的通话呼入允许名单移除后，可解除冲突。 |
| [addOutgoingCallPolicyNumbers](arkts-mdm-telephonymanager-addoutgoingcallpolicynumbers-f.md#addoutgoingcallpolicynumbers) | 添加通话呼出的允许或禁用名单，如果不添加名单，任意号码都可以呼出，添加后只有名单内的号码允许或禁止呼出。  以下情况下，通过本接口添加通话呼出的允许或禁用名单，会报策略冲突：  1. 已经通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy)接口禁用了设备通话能力，再通过本接口添加通话呼出的禁用或允许名单，返回203错误码。通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy)接口解除禁用设备通话能力后，可解除冲突。2. 已经通过本接口设置了通话呼出的禁用名单，再通过本接口添加通话呼出允许名单，返回9200010错误码。通过[removeOutgoingCallPolicyNumbers](arkts-mdm-telephonymanager-removeoutgoingcallpolicynumbers-f.md#removeoutgoingcallpolicynumbers)接口将之前设置的通话呼出禁用名单移除后，可解除冲突。3. 已经通过本接口设置了通话呼出的允许名单，再通过本接口添加通话呼出禁用名单，返回9200010错误码。通过[removeOutgoingCallPolicyNumbers](arkts-mdm-telephonymanager-removeoutgoingcallpolicynumbers-f.md#removeoutgoingcallpolicynumbers)接口将之前设置的通话呼出允许名单移除后，可解除冲突。 |
| [addReceiveSmsPolicyNumbers](arkts-mdm-telephonymanager-addreceivesmspolicynumbers-f.md#addreceivesmspolicynumbers) | 添加接收短信的允许或禁用名单 |
| [addSendSmsPolicyNumbers](arkts-mdm-telephonymanager-addsendsmspolicynumbers-f.md#addsendsmspolicynumbers) | 添加发送短信的允许或禁用名单 |
| [deactiveSim](arkts-mdm-telephonymanager-deactivesim-f.md#deactivesim) | 停用指定卡槽SIM卡。停用该SIM卡，无法使用该卡槽的SIM卡接打电话，收发短信，上网。该接口需要插入SIM卡并关闭飞行模式才能成功调用。 |
| [getDefaultData](arkts-mdm-telephonymanager-getdefaultdata-f.md#getdefaultdata) | 获取设备当前默认使用的数据流量卡卡槽ID。未插卡或者飞行模式下会获取上一次使用的数据流量卡卡槽ID、设备从未设置过默认数据流量卡场景下，该接口返回默认卡槽1，值为0。 |
| [getIncomingCallPolicyNumbers](arkts-mdm-telephonymanager-getincomingcallpolicynumbers-f.md#getincomingcallpolicynumbers) | 获取通话呼入的允许或禁用名单。 |
| [getOutgoingCallPolicyNumbers](arkts-mdm-telephonymanager-getoutgoingcallpolicynumbers-f.md#getoutgoingcallpolicynumbers) | 获取通话呼出的允许或禁用名单。 |
| [getReceiveSmsPolicyNumbers](arkts-mdm-telephonymanager-getreceivesmspolicynumbers-f.md#getreceivesmspolicynumbers) | 查询接收短信允许或禁用名单 |
| [getSendSmsPolicyNumbers](arkts-mdm-telephonymanager-getsendsmspolicynumbers-f.md#getsendsmspolicynumbers) | 查询发送短信的允许或禁用名单 |
| [hangupCalling](arkts-mdm-telephonymanager-hangupcalling-f.md#hangupcalling) | 挂断当前通话。仅支持运营商通话，不包括畅联等。 |
| [isSimDisabled](arkts-mdm-telephonymanager-issimdisabled-f.md#issimdisabled) | 查询指定卡槽是否禁用。 |
| [removeIncomingCallPolicyNumbers](arkts-mdm-telephonymanager-removeincomingcallpolicynumbers-f.md#removeincomingcallpolicynumbers) | 移除通话呼入的允许或禁用名单，若在该名单尚未设置时进行移除，则会移除失败。  以下情况下，通过本接口移除通话呼入的允许或禁用名单，会报策略冲突：  1. 已经通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy)接口禁用了设备通话能力，再通过本接口移除通话呼入的禁用或允许名单，返回203错误码。通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy)接口解除禁用设备通话能力后，可解除冲突。 |
| [removeOutgoingCallPolicyNumbers](arkts-mdm-telephonymanager-removeoutgoingcallpolicynumbers-f.md#removeoutgoingcallpolicynumbers) | 移除通话呼出的允许或禁用名单，若在该名单尚未设置时进行移除，则会移除失败。  以下情况下，通过本接口移除通话呼出的允许或禁用名单，会报策略冲突：  已经通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy)接口禁用了设备通话能力，再通过本接口移除通话呼出的禁用或允许名单，返回203错误码。通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy)接口解除禁用设备通话能力后，可解除冲突。 |
| [removeReceiveSmsPolicyNumbers](arkts-mdm-telephonymanager-removereceivesmspolicynumbers-f.md#removereceivesmspolicynumbers) | 移除接收短信的允许或禁用名单 |
| [removeSendSmsPolicyNumbers](arkts-mdm-telephonymanager-removesendsmspolicynumbers-f.md#removesendsmspolicynumbers) | 移除发送短信允许或禁用名单 |
| [setDefaultData](arkts-mdm-telephonymanager-setdefaultdata-f.md#setdefaultdata) | 设置指定卡槽的SIM卡为默认数据流量卡，设备将使用指定卡槽的SIM卡流量上网。该接口需要插入SIM卡并关闭飞行模式才能成功调用。 |
| [setSimDisabled](arkts-mdm-telephonymanager-setsimdisabled-f.md#setsimdisabled) | 禁用指定卡槽的SIM卡。 |
| [setSimEnabled](arkts-mdm-telephonymanager-setsimenabled-f.md#setsimenabled) | 解除指定卡槽的SIM卡禁用。使用setSimDisabled禁用SIM卡后，再用setSimEnabled启用SIM卡，需要到设置-移动网络-SIM卡管理界面手动打开SIM卡开关。 |

