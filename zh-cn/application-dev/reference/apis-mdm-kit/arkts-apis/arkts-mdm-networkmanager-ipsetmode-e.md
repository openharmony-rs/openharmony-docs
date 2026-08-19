# IpSetMode

以太网连接模式。

**起始版本：** 23

<!--Device-networkManager-enum IpSetMode--><!--Device-networkManager-enum IpSetMode-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## STATIC

```TypeScript
STATIC = 0
```

以太网连接静态配置网络信息，设置为该模式时，需要同步设置IP地址、子网掩码、默认网关、DNS服务器。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IpSetMode-STATIC = 0--><!--Device-IpSetMode-STATIC = 0-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## DHCP

```TypeScript
DHCP = 1
```

以太网连接动态配置网络信息，设置为该模式时，由网络中的DHCP服务器自动分配IP地址等信息。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IpSetMode-DHCP = 1--><!--Device-IpSetMode-DHCP = 1-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

