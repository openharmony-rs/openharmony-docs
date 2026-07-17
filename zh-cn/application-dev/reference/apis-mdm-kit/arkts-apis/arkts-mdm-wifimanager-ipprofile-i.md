# IpProfile

IP配置信息。

**起始版本：** 12

<!--Device-wifiManager-interface IpProfile--><!--Device-wifiManager-interface IpProfile-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { wifiManager } from '@kit.MDMKit';
```

## dnsServers

```TypeScript
dnsServers: number[]
```

DNS服务器，数组内最多包含首选DNS服务器和备用DNS服务器两个地址。地址值范围0.0.0.0到255.255.255.255。

**类型：** number[]

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IpProfile-dnsServers: number[]--><!--Device-IpProfile-dnsServers: number[]-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## domains

```TypeScript
domains: Array<string>
```

域信息。

**类型：** Array<string>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IpProfile-domains: Array<string>--><!--Device-IpProfile-domains: Array<string>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## gateway

```TypeScript
gateway: number
```

默认网关，十进制表示，通常是路由器的IP地址。地址值范围0.0.0.0到255.255.255.255。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IpProfile-gateway: number--><!--Device-IpProfile-gateway: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## ipAddress

```TypeScript
ipAddress: number
```

IP地址，十进制表示，正常点分十进制写法为192.168.1.1，对应的十进制为3232235777。地址值范围0.0.0.0到255.255.255.255。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IpProfile-ipAddress: number--><!--Device-IpProfile-ipAddress: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## prefixLength

```TypeScript
prefixLength: number
```

子网掩码。地址值范围0.0.0.0到255.255.255.255。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IpProfile-prefixLength: number--><!--Device-IpProfile-prefixLength: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

