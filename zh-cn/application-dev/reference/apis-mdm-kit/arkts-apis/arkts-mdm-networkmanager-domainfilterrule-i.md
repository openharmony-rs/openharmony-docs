# DomainFilterRule

域名过滤规则。

API version 21及之前版本，仅支持IPv4。从API version 22开始，支持IPv4和IPv6。

从API version 23开始，支持[LogType](arkts-mdm-networkmanager-logtype-e.md)。

**起始版本：** 12

<!--Device-networkManager-interface DomainFilterRule--><!--Device-networkManager-interface DomainFilterRule-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { networkManager } from '@kit.MDMKit';
```

## action

```TypeScript
action?: Action
```

接收或者丢弃数据包。

添加域名过滤规则时必填；

移除域名过滤规则时非必填，当值为空时，表示清空所有的匹配[Action](arkts-mdm-networkmanager-action-e.md)规则的链，且domainName，appUid也必须传入空值。

**类型：** Action

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DomainFilterRule-action?: Action--><!--Device-DomainFilterRule-action?: Action-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## appUid

```TypeScript
appUid?: string
```

应用uid。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DomainFilterRule-appUid?: string--><!--Device-DomainFilterRule-appUid?: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## direction

```TypeScript
direction?: Direction
```

规则链。

添加域名过滤规则时非必填；当值设为输出链或输入链时，实际效果为输出链。设为转发链时，appUid需设置为空，否则会报401错误码。

移除域名过滤规则时非必填，当值为空时，表示清空所有的[Direction](arkts-mdm-networkmanager-direction-e.md)链，且domainName，appUid也必须传入空值。

**类型：** Direction

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DomainFilterRule-direction?: Direction--><!--Device-DomainFilterRule-direction?: Direction-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## domainName

```TypeScript
domainName?: string
```

域名。添加域名过滤规则时必填。支持域名分段匹配，例如，domainName传入`example.com`，那么`example.com`、`www.example.com`、`www.test.example.com`会被匹配，`linkexample.com`不会被匹配。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DomainFilterRule-domainName?: string--><!--Device-DomainFilterRule-domainName?: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## family

```TypeScript
family?: number
```

IP协议版本。支持取值为1或2，取值为1表示IPv4，取值为2表示IPv6。取值应为[1,2]内的整数。

**类型：** number

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DomainFilterRule-family?: number--><!--Device-DomainFilterRule-family?: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## logType

```TypeScript
logType?: LogType
```

日志类型，当前仅支持配置NFLOG类型，该参数仅支持PC/2in1设备。添加防火墙过滤规则时，此参数非必填。若填写，仅在丢弃或拒绝数据包时生效。<!--RP1--><!--RP1End-->移除防火墙过滤规则时，当清空某条链时非必填，不影响整条链的清空；当移除单条规则时，是否填写必须与该规则一致，否则可能导致过滤规则已经移除，但是日志还在记录的问题；相同过滤规则移除时必须按添加时的顺序移除。获取防火墙过滤规则时，仅日志生效的场景可以获取到logType字段。

**类型：** LogType

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DomainFilterRule-logType?: LogType--><!--Device-DomainFilterRule-logType?: LogType-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

