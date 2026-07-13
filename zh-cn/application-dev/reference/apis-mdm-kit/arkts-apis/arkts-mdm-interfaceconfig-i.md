# InterfaceConfig

以太网的网络接口配置。仅支持IPv4。

**起始版本：** 23

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## dnsServers

```TypeScript
dnsServers?: string
```

DNS服务地址，地址值范围0.0.0.0到255.255.255.255（DHCP模式无需配置），多地址间用“,”隔开。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## gateway

```TypeScript
gateway?: string
```

网关，地址值范围0.0.0.0到255.255.255.255（DHCP模式无需配置）。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## ipAddress

```TypeScript
ipAddress?: string
```

静态IP地址，地址值范围0.0.0.0到255.255.255.255（DHCP模式无需配置）。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## ipSetMode

```TypeScript
ipSetMode: IpSetMode
```

以太网连接配置模式。

**类型：** IpSetMode

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## netMask

```TypeScript
netMask?: string
```

子网掩码，地址值范围0.0.0.0到255.255.255.255（DHCP模式无需配置）。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

