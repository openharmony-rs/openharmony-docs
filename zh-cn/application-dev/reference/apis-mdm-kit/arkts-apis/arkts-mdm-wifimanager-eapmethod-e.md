# EapMethod

表示EAP认证方式的枚举。
> **说明**：  
>  
> 当前仅支持使用EAP_PEAP、EAP_TLS两种认证方式，其他暂不支持。

**起始版本：** 12

<!--Device-wifiManager-enum EapMethod--><!--Device-wifiManager-enum EapMethod-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## EAP_NONE

```TypeScript
EAP_NONE = 0
```

未指定。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EapMethod-EAP_NONE = 0--><!--Device-EapMethod-EAP_NONE = 0-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## EAP_PEAP

```TypeScript
EAP_PEAP = 1
```

PEAP类型，受保护的可扩展认证协议。先建立安全的TLS隧道、然后进行简单认证。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EapMethod-EAP_PEAP = 1--><!--Device-EapMethod-EAP_PEAP = 1-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## EAP_TLS

```TypeScript
EAP_TLS = 2
```

TLS类型，传输层安全协议。双向证书认证。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EapMethod-EAP_TLS = 2--><!--Device-EapMethod-EAP_TLS = 2-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## EAP_TTLS

```TypeScript
EAP_TTLS = 3
```

TTLS类型，隧道传输层安全协议。与PEAP类似，但后续隧道内部认证方法更加丰富。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EapMethod-EAP_TTLS = 3--><!--Device-EapMethod-EAP_TTLS = 3-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## EAP_PWD

```TypeScript
EAP_PWD = 4
```

密码。当eapMethod为EAP_PEAP或EAP_PWD时，该字段不能为空串，最大长度为128字节。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EapMethod-EAP_PWD = 4--><!--Device-EapMethod-EAP_PWD = 4-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## EAP_SIM

```TypeScript
EAP_SIM = 5
```

SIM类型，使用手机SIM卡中的密钥和算法进行认证。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EapMethod-EAP_SIM = 5--><!--Device-EapMethod-EAP_SIM = 5-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## EAP_AKA

```TypeScript
EAP_AKA = 6
```

AKA类型，使用USIM卡（3G/4G/5G SIM卡）中的增强密钥和算法进行认证。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EapMethod-EAP_AKA = 6--><!--Device-EapMethod-EAP_AKA = 6-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## EAP_AKA_PRIME

```TypeScript
EAP_AKA_PRIME = 7
```

AKA Prime类型，EAP-AKA增强版，在密钥派生中绑定网络名称。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EapMethod-EAP_AKA_PRIME = 7--><!--Device-EapMethod-EAP_AKA_PRIME = 7-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## EAP_UNAUTH_TLS

```TypeScript
EAP_UNAUTH_TLS = 8
```

UNAUTH TLS类型，单向认证（仅认证客户端）和加密通道。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EapMethod-EAP_UNAUTH_TLS = 8--><!--Device-EapMethod-EAP_UNAUTH_TLS = 8-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

