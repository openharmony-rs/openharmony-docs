# AddFilterRule（系统接口）

添加网络包过滤规则。

**起始版本：** 10

<!--Device-networkManager-interface AddFilterRule--><!--Device-networkManager-interface AddFilterRule-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { networkManager } from '@kit.MDMKit';
```

## action

```TypeScript
action: Action
```

接收或者丢弃数据包。

**类型：** Action

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AddFilterRule-action: Action--><!--Device-AddFilterRule-action: Action-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

## destAddr

```TypeScript
destAddr?: string
```

ip目标地址。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AddFilterRule-destAddr?: string--><!--Device-AddFilterRule-destAddr?: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

## destPort

```TypeScript
destPort?: string
```

ip目标端口。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AddFilterRule-destPort?: string--><!--Device-AddFilterRule-destPort?: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

## direction

```TypeScript
direction: Direction
```

规则链。

**类型：** Direction

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AddFilterRule-direction: Direction--><!--Device-AddFilterRule-direction: Direction-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

## method

```TypeScript
method: AddMethod
```

添加策略。

**类型：** AddMethod

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AddFilterRule-method: AddMethod--><!--Device-AddFilterRule-method: AddMethod-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

## protocol

```TypeScript
protocol?: Protocol
```

网络协议。

**类型：** Protocol

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AddFilterRule-protocol?: Protocol--><!--Device-AddFilterRule-protocol?: Protocol-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

## ruleNo

```TypeScript
ruleNo?: number
```

规则序号。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AddFilterRule-ruleNo?: number--><!--Device-AddFilterRule-ruleNo?: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

## srcAddr

```TypeScript
srcAddr?: string
```

ip源地址。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AddFilterRule-srcAddr?: string--><!--Device-AddFilterRule-srcAddr?: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

## srcPort

```TypeScript
srcPort?: string
```

ip源端口。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AddFilterRule-srcPort?: string--><!--Device-AddFilterRule-srcPort?: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

## uid

```TypeScript
uid?: string
```

应用uid。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AddFilterRule-uid?: string--><!--Device-AddFilterRule-uid?: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

