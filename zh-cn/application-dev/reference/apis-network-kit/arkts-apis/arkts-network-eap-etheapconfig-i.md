# EthEapConfig

```TypeScript
interface EthEapConfig
```

表示802.1X以太网EAP配置，包括EAP配置文件和功能切换。

**起始版本：** 26.0.1

<!--Device-eap-interface EthEapConfig--><!--Device-eap-interface EthEapConfig-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap

## 导入模块

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## autoAuth

```TypeScript
autoAuth: boolean
```

是否在连接网线或启动时自动启动身份验证。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EthEapConfig-autoAuth: boolean--><!--Device-EthEapConfig-autoAuth: boolean-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap

## enabled

```TypeScript
enabled: boolean
```

802.1X特性是否使能。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EthEapConfig-enabled: boolean--><!--Device-EthEapConfig-enabled: boolean-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap

## locked

```TypeScript
locked: boolean
```

配置是否被锁定。锁定时，除解锁外，其他修改均被拒绝。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EthEapConfig-locked: boolean--><!--Device-EthEapConfig-locked: boolean-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap

## profile

```TypeScript
profile: EthEapProfile
```

EAP配置文件信息。

**类型：** [EthEapProfile](arkts-network-eap-etheapprofile-i.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EthEapConfig-profile: EthEapProfile--><!--Device-EthEapConfig-profile: EthEapProfile-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap
