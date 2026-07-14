# IpProfile

IP配置信息。

**起始版本：** 12

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## dnsServers

```TypeScript
dnsServers: number[]
```

DNS服务器，数组内最多包含首选DNS服务器和备用DNS服务器两个地址。地址值范围0.0.0.0到255.255.255.255。

**类型：** number[]

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## domains

```TypeScript
domains: Array<string>
```

域信息。

**类型：** Array<string>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## gateway

```TypeScript
gateway: number
```

默认网关，十进制表示，通常是路由器的IP地址。地址值范围0.0.0.0到255.255.255.255。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## ipAddress

```TypeScript
ipAddress: number
```

IP地址，十进制表示，正常点分十进制写法为192.168.1.1，对应的十进制为3232235777。地址值范围0.0.0.0到255.255.255.255。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## prefixLength

```TypeScript
prefixLength: number
```

子网掩码。地址值范围0.0.0.0到255.255.255.255。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

